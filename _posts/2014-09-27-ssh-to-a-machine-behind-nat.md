---
id: 7
title: SSH to a machine behind NAT
date: 2014-09-27T02:55:33+08:00
author: Siddharth
layout: post
guid: http://siddharthgoel88.wordpress.com/?p=7
permalink: /2014/09/ssh-to-a-machine-behind-nat/
geo_public:
  - "0"
dsq_thread_id:
  - "3273149380"
categories:
  - Tech
tags:
  - how to
  - Linux
  - mac
  - NAT
  - ngrok
  - port forwarding
  - reverse-ssh
  - shell
  - ssh
---
<p style="text-align: justify;">
  SSHing to a machine behind NAT has generally been a daunting task. One of the common way that people tend to use is through forwarding a port from router on to the machine. But it is not always the case that a person has access to router configuration settings of his network. <!--more-->I recently stumbled upon an awesome tool named 
  
  <a href="https://ngrok.com/" target="_blank" rel="noopener">ngrok</a> which solves this problem very elegantly. Even though this tool&#8217;s mail purpose is to take your localhost online but it has many other features out of which we will leverage one now. Let do it:
</p>

<li style="text-align: justify;">
  Download ngrok to the Linux or Mac machine you want to ssh to. You can download it from <a title="here" href="https://ngrok.com/download" target="_blank" rel="noopener">here</a>.
</li>
<li style="text-align: justify;">
  Unzip it by going to the folder it is downloaded to and executing the following command &#8211;<code>&lt;br />
unzip ngrok.zip&lt;br />
</code>
</li>
<li style="text-align: justify;">
  After extracting run the following command &#8211;<code>&lt;br />
./ngrok -proto=tcp 22&lt;br />
</code><br /> Running the above command will take you to a screen like below &#8211;<a href="http://siddharthgoel.com/wp-content/uploads/2014/09/ngrok.png"><br /> </a><a href="https://sidd.io/wp-content/uploads/2014/09/ngrok.png"><img class="alignnone wp-image-12 size-full" src="https://sidd.io/wp-content/uploads/2014/09/ngrok.png" alt="" width="577" height="181" srcset="https://sidd.io/wp-content/uploads/2014/09/ngrok.png 577w, https://sidd.io/wp-content/uploads/2014/09/ngrok-300x94.png 300w" sizes="(max-width: 577px) 100vw, 577px" /></a><br /> In the above screenshot we can see that port 58339 on ngrok.com is forwarded to port 22 of our Linux/Mac machine.
</li>
<li style="text-align: justify;">
  So now you are ready to SSH to your machine from some other machine. Use the following command to ssh &#8211; <pre class="brush: bash; title: ; notranslate" title="">
ssh -p &lt;nrgok_port&gt; &lt;local_machine_username&gt;@ngrok.com
</pre>
  
  <p>
    Like in the case of screen shot above I need to type in the following command &#8211;
  </p>
  
  <pre class="brush: bash; title: ; notranslate" title="">
ssh -p 58339 myusername@ngrok.com
</pre>
</li>

Enjoy SSHing fellas !!