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
<pre><code>&lt;repositories&gt;
    &lt;repository&gt;
        &lt;id&gt;maven.nikr.net&lt;/id&gt;
        &lt;name&gt;maven.nikr.net&lt;/name&gt;
        &lt;url&gt;http://maven.nikr.net/&lt;/url&gt;
    &lt;/repository&gt;
&lt;/repositories&gt;
...
&lt;dependencies&gt;
    &lt;dependency&gt;
        &lt;groupId&gt;net.nikr&lt;/groupId&gt;
        &lt;artifactId&gt;dds&lt;/artifactId&gt;
        &lt;version&gt;1.0.0&lt;/version&gt;
    &lt;/dependency&gt;
&lt;/dependencies&gt;
</code></pre>
<br>
<br>
Code Example:<br>
<pre><code>File file = new File("image.dds");
BufferedImage image = null;
try {
	image = ImageIO.read(file);
} catch (IOException ex) {
	System.out.println("Failed to load: "+file.getName());
}
</code></pre>
<br>
Advanced Code Example:<br>
<pre><code>public BufferedImage read(File file, int imageIndex) throws IOException{
	Iterator&lt;ImageReader&gt; iterator = ImageIO.getImageReadersBySuffix("dds");
	if (iterator.hasNext()){
		ImageReader imageReader = iterator.next();
		imageReader.setInput(new FileImageInputStream(file));
		int max = imageReader.getNumImages(true);
		if (imageIndex &lt; max) return imageReader.read(imageIndex);
	}
	return null;
}
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