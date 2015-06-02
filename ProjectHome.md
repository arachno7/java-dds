# Java DDS ImageIO Plugin. #
## Supports reading of: ##
  * **DXT1** / BC1
  * **DXT2** / BC2
  * **DXT5** / BC3
  * **ATI1** / BC4
  * **ATI2** / BC5
  * Most **Uncompressed** formats
_See all [supported formats](SupportedFormats.md)._<br>
<br>
<h2>Does <b>not</b> support:</h2>
<ul><li>Writing<br>
<br>
<h2>Info</h2>
The library is not actively being worked on, except for bug fixes and contributions.<br>
<br>
<h2>Help</h2>
To use in a maven project:<br>
<pre><code>&lt;repositories&gt;<br>
    &lt;repository&gt;<br>
        &lt;id&gt;maven.nikr.net&lt;/id&gt;<br>
        &lt;name&gt;maven.nikr.net&lt;/name&gt;<br>
        &lt;url&gt;http://maven.nikr.net/&lt;/url&gt;<br>
    &lt;/repository&gt;<br>
&lt;/repositories&gt;<br>
...<br>
&lt;dependencies&gt;<br>
    &lt;dependency&gt;<br>
        &lt;groupId&gt;net.nikr&lt;/groupId&gt;<br>
        &lt;artifactId&gt;dds&lt;/artifactId&gt;<br>
        &lt;version&gt;1.0.0&lt;/version&gt;<br>
    &lt;/dependency&gt;<br>
&lt;/dependencies&gt;<br>
</code></pre>
<br>
<br>
Code Example:<br>
<pre><code>File file = new File("image.dds");<br>
BufferedImage image = null;<br>
try {<br>
	image = ImageIO.read(file);<br>
} catch (IOException ex) {<br>
	System.out.println("Failed to load: "+file.getName());<br>
}<br>
</code></pre>
<br>
Advanced Code Example:<br>
<pre><code>public BufferedImage read(File file, int imageIndex) throws IOException{<br>
	Iterator&lt;ImageReader&gt; iterator = ImageIO.getImageReadersBySuffix("dds");<br>
	if (iterator.hasNext()){<br>
		ImageReader imageReader = iterator.next();<br>
		imageReader.setInput(new FileImageInputStream(file));<br>
		int max = imageReader.getNumImages(true);<br>
		if (imageIndex &lt; max) return imageReader.read(imageIndex);<br>
	}<br>
	return null;<br>
}<br>
</code></pre>
<br>
<h2>Bugs</h2>
You can submit a bug report by creating a <a href='http://code.google.com/p/java-dds/issues/entry'>new issue</a>.<br>
<br>
<h2>Special Thanks</h2>
Java DDS ImageIO Plugin is based on code from the <a href='http://code.google.com/p/gimp-dds/'>GIMP DDS Plugin</a>.<br>
<br>
<h2>Contribute</h2>
Want to join the project?<br>
Send an email to niklaskr@gmail.com<br>