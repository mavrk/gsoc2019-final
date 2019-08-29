## About the project

**Eclipse SWTChart Project - Extending the export options**

See Eclipse SWTChart on [Eclipse](https://projects.eclipse.org/projects/science.swtchart), [Github](https://github.com/eclipse/swtchart)  
See this project on [Google Summer of code](https://summerofcode.withgoogle.com/projects/#4820028082356224)  
Mentor - [Philip Wenig](https://github.com/eclipse/swtchart/commits?author=eselmeister)

**Project Goals and deliverables**
1. Add SVG export option
2. Add PDF and EPS export option

## SVG Export
SVG files are nothing but XML graphics files. We can generate SVG files for our charts using the [Apache XMLGraphics](https://xmlgraphics.apache.org/) project. This project has an open-source license and is already available under Eclipse Orbit.  
 
The Apache Batik is a sub-project of the Apache XMLGraphics project and has a built in SVGGenerator class ​https://xmlgraphics.apache.org/batik/using/svg-generator.html  
 On the Java platform, all rendering goes through the [Graphics2D](https://docs.oracle.com/javase/1.5.0/docs/api/java/awt/Graphics2D.html) abstract class, which offers methods such as drawRect, fillRect, and drawString. There are specialized implementations of this abstract class for each type of output, such as a screen or a printer. SVGGraphics2D is a new implementation of that interface that generates SVG content instead of drawing to a screen or a printer.

In order to use this interface we first need to create a Graphics2D implementation of our chart which involves converting _org.eclipse.swt.gc_ object to _java.awt.Graphics2D_ 

PR for this change : https://github.com/eclipse/swtchart/pull/61

Once we have created a Graphics2D object, we can use it to create our SVG file. 

PR for this : https://github.com/eclipse/swtchart/pull/67

Some sample exports: 
<img src="./as.svg" height="380" width="950">
<img src="./as2.svg" height="350" width="950">
<img src="./as3.svg" height="550" width="950">

## EPS and PDF Export
Exporting to EPS and PDF is not very straightforward like exporting to SVG. Though the Apache XMLGraphics project has an option to create EPS files, but the functionality is pretty basic. The other option is to create a SVG file and transcode it to EPS or PDF using Apache FOP. Unfortunately, Apache FOP is not a part of Eclipse Orbit and isn't supported out-of-the box like Apache Batik. The good news is that the EPSTranscoder and PDFTranscoder will be moved to the Transcoder package in Batik and in a future release, we can extend this functionality in SWTChart.

Some sample exports:
[PDF Export](https://github.com/mavrk/gsoc2019-final/master/scatter.pdf)
[EPS Export](https://github.com/mavrk/gsoc2019-final/master/scatter.eps)

### Support or Contact

Sanatt Abrol
sanatt.abrol.in@gmail.com
https://github.com/mavrk
