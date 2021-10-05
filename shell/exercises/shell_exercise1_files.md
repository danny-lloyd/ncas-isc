<!-- JavaScript Bundle with Popper -->
<head>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-/bQdsTh/da6pkI1MST/rWKFNjaCP5gBSY4sEBT38Q/9RBh9AH40zEOg7Hlq2THRZ" crossorigin="anonymous"></script>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-F3w7mX95PdgyTmZZMECAngseQB83DfGTowi0iMjiWaeVhAn4FJkqJByhZMI3AhiU" crossorigin="anonymous">

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>

    <link href="exercise.css" rel="stylesheet">
</head>
    <body>
      <div class="container">

<h1>Exercise 1: Exploring the file system</h1>

<h2>Aim</h2>
Login and look at some files. 
<h2>Issues covered</h2>
Commands: <code>pwd, ls, gedit, cd, cp, mv, mkdir, rm, rmdir, man</code>. What’s in  <code>/tmp</code>, <code>/</code> and <code>/etc</code>
<h2>Instructions</h2>

<ol>

<li>Let's get started by logging in. </li>
    <ol>
<li>Login to the laptop (you should have a username and password).</li>
<li>Start a terminal window.</li>
</ol>


<li>Have a look around your home directory.  Try the following commands.
<pre>pwd
ls 
ls -l
ls -a
ls ..
ls shell
</pre>
</li>

<div id="sol1" class="solution">
<pre> 
$ pwd
/Users/sjp23/play/workshop_shell
$ ls
acsoe
$ ls -l
total 0
drwxr-x---  16 sjp23  staff  544 26 Feb 16:21 acsoe
$ ls -a
.	..	acsoe
$ ls ..
badc			dataman		workshop_shell
$ ls acsoe
00README	eae-96	ease-96	freetex-96	hillcloud-96	lterm
c-130	eae-97	ease-97	freetex-98	hillcloud-97	ozprof
</pre>
</div>
<button id="b_sol1" class="btn btn-primary">Solution</button> <script>$( "#b_sol1" ).click(function() {$( "#sol1" ).toggle( "slow" );});</script>

<li>Let’s have a look somewhere else. Change directory to <code>acsoe</code>. 
<pre>
$ cd ncas-isc/shell/acsoe
</pre>
Now repeat (2)
</li>

<div id="sol2" class="solution">
<pre>
$ cd acsoe
$ pwd
/Users/sjp23/play/workshop_shell/acsoe
$ ls
00README	eae-96	ease-96	freetex-96	hillcloud-96	lterm
c-130	eae-97	ease-97	freetex-98	hillcloud-97	ozprof
$ ls -l
total 8
-rwxr-x---  1 sjp23  staff  190 26 Feb 16:21 00README
drwxr-x---  8 sjp23  staff  272 26 Feb 16:20 c-130
drwxr-x---  8 sjp23  staff  272 26 Feb 16:20 eae-96
drwxr-x---  8 sjp23  staff  272 26 Feb 16:21 eae-97
drwxr-x---  7 sjp23  staff  238 26 Feb 16:21 ease-96
drwxr-x---  6 sjp23  staff  204 26 Feb 16:21 ease-97
drwxr-x---  6 sjp23  staff  204 26 Feb 16:21 freetex-96
drwxr-x---  6 sjp23  staff  204 26 Feb 16:21 freetex-98
drwxr-x---  8 sjp23  staff  272 26 Feb 16:21 hillcloud-96
drwxr-x---  9 sjp23  staff  306 26 Feb 16:21 hillcloud-97
drwxr-x---  6 sjp23  staff  204 26 Feb 16:21 lterm
drwxr-x---  6 sjp23  staff  204 26 Feb 16:21 ozprof
$ ls -a
.	.summary	eae-96	ease-97	 hillcloud-96	ozprof
..	00README	eae-97	freetex-96 hillcloud-97	.checksums	
c-130		ease-96	freetex-98 lterm
$ ls ..
acsoe
</pre>
</div>
<button id="b_sol2" class="btn btn-primary">Solution</button> <script>$( "#b_sol2" ).click(function() {$( "#sol2" ).toggle( "slow" );});</script>


<li>Manipulating some files and directories.</li>
<ol>
<li>Make a file called "myfile" in "/tmp" with gedit.</li>
<li>Make a subdirectory in "/tmp" called "mydir"</li>
<li>Rename the file "myfile.txt" and the subdirectory "X"</li>
<li>Copy "myfile.txt" into the "X" subdirectory</li>
<li>Tidy up - delete the file and subdirectory</li>
<li>Use the "man ls" command to find other listing options. Experiment… have a look in "/", and "/etc".</li>
<li>How not to do it:</li>
<li>Use cd with no arguments to jump back to your home directory.</li>
<li>Go into the "pain" directory</li>
<li>Use ls to see what files are here</li>
<li>Move them to more sensible names (if you can).</li>
</ol>


<div id="sol3" class="solution">
<pre>
<span class="cmd">$ cd /tmp</span>
<span class="cmd">$ gedit myfile</span>
<span class="cmd">$ ls</span>
myfile
test.txt

<span class="cmd">$ mkdir mydir</span>
<span class="cmd">$ ls -l</span>
total 56
drwxr-xr-x  2 sjp23           wheel     68 26 Feb 17:14 mydir
-rw-r--r--  1 sjp23           wheel      7 26 Feb 17:13 myfile

<span class="cmd">$ mv myfile X</span>
<span class="cmd">$ mv X myfile.txt</span>
<span class="cmd">$ mv mydir X</span>

<span class="cmd">$ cp myfile.txt  X</span>
<span class="cmd">$ ls -l</span>
total 56
drwxr-xr-x  3 sjp23           wheel    102 26 Feb 17:15 X
-rw-r--r--  1 sjp23           wheel      7 26 Feb 17:13 myfile.txt

<span class="cmd">$ ls -l X</span>
total 8
-rw-r--r--  1 sjp23  wheel  7 26 Feb 17:21 myfile.txt
<span class="cmd">$ rm X/myfile.txt </span>
<span class="cmd">$ rmdir X</span>

<span class="cmd">$ cd</span>
<span class="cmd">$ cd pain</span>
<span class="cmd">$ ls -l</span>
total 0
-rw-r--r--  1 sjp23  staff  0 20 Mar 12:48 -l
-rw-r--r--  1 sjp23  staff  0 20 Mar 12:49 What the $
-rw-r--r--  1 sjp23  staff  0 20 Mar 12:53 Ω
<span class="cmd">$ mv -l  L</span>
<span class="cmd">$ mv What\ the\ \$ What_the_dollar</span>
<span class="cmd">$ mv ? omega</span>
<span class="cmd">$ ls -l</span>
total 0
-rw-r--r--  1 sjp23  staff  0 20 Mar 12:48 L
-rw-r--r--  1 sjp23  staff  0 20 Mar 12:49 What_the_dollar
-rw-r--r--  1 sjp23  staff  0 20 Mar 12:53 omega  
</pre>
</div>
<button id="b_sol3" class="btn btn-primary">Solution</button> <script>$( "#b_sol3" ).click(function() {$( "#sol3" ).toggle( "slow" );});</script>
</ol>