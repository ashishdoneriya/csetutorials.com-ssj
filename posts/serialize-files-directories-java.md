---
title: How to Serialize files and directories in Java
created: 2016-10-13T12:42:40+05:30
author: ashishdoneriya
description: Serialize and Deserialize files and directories in java. Write the contents of whole directory in a single file.
permalink: /serialize-files-directories-java.html
categories:
  - big-data
tags:
  - java
updated: 2016-10-13T12:42:40+05:30
---

Code to serialize a directory or a file.

#### Class Node

```java
package com.csetutorials;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.Serializable;
import java.util.ArrayList;
import java.util.List;

public class Node implements Serializable {

  private static final long serialVersionUID = 1L;

  private boolean isDirectory;

  private String filename;

  // In case the node is a directory, here are its child nodes
  private List&lt;Node&gt; list;

  // In case the node is a file, this byte array is its content
  private byte[] bytes;

  public Node() {
  }

  public Node(String filePath) throws IOException {
    Node node = getNode(new File(filePath));
    this.isDirectory = node.isDirectory;
    this.filename = node.filename;
    this.list = node.list;
    this.bytes = node.bytes;
  }

  public void writeContentsToDir(String outputPath) throws IOException {
    if (!outputPath.endsWith(File.separator)) {
      outputPath = outputPath + File.separator;
    }
    writeToFile(outputPath, this);
  }

  private void writeToFile(String parentPath, Node node) throws IOException {
    if (node.isDirectory) {
      parentPath = parentPath + File.separator + node.filename;
      for (Node df : node.list) {
        writeToFile(parentPath, df);
      }
    } else {
      new File(parentPath).mkdirs();
      File file = new File(parentPath, node.filename);
      file.setReadable(true, false);
      file.setWritable(true, false);
      
      FileOutputStream fos = null;
      try {
        fos = new FileOutputStream(file);
        fos.write(node.bytes);
        fos.flush();
      } finally {
        if (fos != null) {
          fos.close();
        }
      }
    }
  }

  private Node getNode(File file) throws IOException {

    Node node = new Node();
    node.filename = file.getName();

    if (file.isFile()) {
      node.isDirectory = false;
      node.bytes = getBytes(file);
    } else {
      node.isDirectory = true;
      for (File f : file.listFiles()) {
        node.addToList(getNode(f));
      }
    }
    return node;
  }

  private void addToList(Node node) {
    if (list == null) {
      list = new ArrayList&lt;Node&gt;();
    }
    list.add(node);
  }

  private byte[] getBytes(File file) throws IOException {
    FileInputStream fileInputStream = null;

    byte[] bytes = new byte[(int) file.length()];

    try {
      // convert file into array of bytes
      fileInputStream = new FileInputStream(file);
      fileInputStream.read(bytes);
      return bytes;
    } finally {
      if (fileInputStream != null) {
        try {
          fileInputStream.close();
        } catch (IOException e) {
          e.printStackTrace();
        }
      }
    }
  }

}
```


#### Class Test

```java
package com.csetutorials;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;

public class Test {

  public static void main(String[] args) throws Exception {
    // Serializing the directory
    Node node = new Node("/home/ashish/Pictures");
    
    // Serializable Object
    Serializable serializable = (Serializable) node;
    
    // Writing the Object/ Directory in a file
    writeToFile(node, "/home/ashish/samples.o");
    
    // Reading the object again from file
    Node node1 = readFromFile("/home/ashish/samples.o");
    
    // Writing the contents of Object back to file system
    node1.writeContentsToDir("/home/ashish/Pictures1");
  }

  private static void writeToFile(Node node, String filepath)
      throws IOException {
    ObjectOutputStream oos = null;
    FileOutputStream fout = null;
    try {
      fout = new FileOutputStream(filepath, true);
      oos = new ObjectOutputStream(fout);
      oos.writeObject(node);
    } finally {
      if (oos != null) {
        oos.close();
      }
    }
  }

  private static Node readFromFile(String filepath)
      throws IOException, ClassNotFoundException {
    ObjectInputStream objectinputstream = null;
    FileInputStream streamIn = null;
    try {
      streamIn = new FileInputStream(filepath);
      objectinputstream = new ObjectInputStream(streamIn);
      Node node = (Node) objectinputstream.readObject();
      return node;
    } finally {
      if (objectinputstream != null) {
        objectinputstream.close();
      }
    }
  }

}
```

