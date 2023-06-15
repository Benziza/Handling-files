# Handling-files

The Java language provides you with the **java.io** package, which contains all the classes you need to deal with files, whether to enter new data in it, extract existing data from it, in addition to creating new files or deleting files.

The process of entering or extracting data from files is called **Streaming data**.

## Concept of Streams in Java

The word Streams means a series of data, which are extracted or inserted into a specific file.

There are two types of Streams: **input stream** and **output stream**.
![alt text](https://harmash.com/tutorials/java/files-io/5398aa87-1273-4955-ab6c-6671807d01ec_pic_1.PNG)

## How to handle files in java

Steps to follow to read data from one file and write it to another file

- Create an object representing the file from which you want to read data.
- Create an object representing the file to which you want to write data.
- You must put all commands that deal with files inside the **try** statement, because the program may encounter several problems when dealing with files, which we will mention to you later.
- Determine the path, name, and file type of the object that represents the file from which the data will be read.
- Determine the path, name, and file type of the object that represents the file in which data will be written.
- Define a variable of type int.
- Using a loop in parallel between the two files, that is, in each cycle of this loop, we read a letter from the first file and put it in the second file.
- Use the read() function to read a character from the first file, then store that character in a variable.
- Using the write() function to write the character in the variable to the second file.
- In the end, you must make sure that the files that you tried to communicate with are closed, whether the copy process succeeds or not, so you must call the close() function in the finally statement to close any object connected to the files so that the files are not exposed to any danger.

## Determine the path of the files you are trying to work with

One of the important things to look out for when working with files is knowing how the operating system you're building your program for handles paths.

![alt text](https://harmash.com/tutorials/java/files-io/9940b635-bd6c-4b34-919d-fdc28fb34ec5_pic_3.PNG)

```
A\\B\\C\\test.txt       //  Mac && Windows

A/B/C/test.txt          // Linux && Unix
```

## The concept of Character Streams in Java

Classes that are classified as Character Streams are designed to handle plain text files that rely on unicode encoding, ie each character in the file is represented by 2 bytes.

There are many classes that belong to Character Streams, but the two most used are **FileReader** and **FileWriter**.\
Exemple :

```
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class Main {

    <!-- Here we put the throws IOException clause because the close()  throw an exception in the main() function. -->
    public static void main(String[] args) throws IOException {

        FileReader in = null;
        FileWriter out = null;

        try {
            in = new FileReader("C:\\MyFiles\\input.txt");
            out = new FileWriter("C:\\MyFiles\\ouput.txt");
            int c;

            while ((c = in.read()) != -1) {
                out.write(c);
            }
        }
        catch(IOException e) {
            System.out.println("There is IOException!");
        }
        finally {
            if (in != null) {
                in.close();
            }
            if (out != null) {
                out.close();
            }
        }

    }

}
```

## Classes designed to handle Character Streams in Java

![alt text](https://harmash.com/tutorials/java/files-io/66dcf019-a953-4225-8b2f-df6571e0a531_pic_6.PNG)
The two most important classes for dealing with Character Streams are the **BufferedReader** class and the **BufferedWriter** class.

## The idea of the buffer

Suppose your program will read, for example, a 10 MB file, which equals 10,485,760 Bytes.

Will you call read() more than **10 million times** to read this file?!
Absolutely not, because if you do that, you will exhaust the processor, memory, and hard disk to read this simple file => solution is **Buffer**.

## Buffer concept

The buffer is a temporary storage space that is created in memory in order to read a large amount of information, and then it is discarded when it is finished.

Now if we go back to the previous example, you could have read 1000 Bytes or more for example every time you call the read() function instead of calling it to read 1 Byte each time.

## Classes

In the following table, we have listed some Character Streams classes that are used to read from files.\
Read :\
https://harmash.com/tutorials/java/files-io \
Write : \
https://harmash.com/tutorials/java/files-io

## The concept of byte streams in java

Classes that are classified as **Byte Streams** are designed to deal with non-text files that store content in the form of a data string of 1 byte (such as PNG, MP4, MP3...) and can transfer regular characters, provided that the characters used consist of 1 byte in order to be transmitted correctly.

There are many classes that belong to Byte Streams, but the two most used are: **FileInputStream** and **FileOutputStream**.

Exemple : Duplicate a video

```
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class Main {

    public static void main(String[] args) throws IOException {

        FileInputStream in = null;
        FileOutputStream out = null;

        try {
            in = new FileInputStream("C:\\MyFiles\\input.MP4");
            out = new FileOutputStream("C:\\MyFiles\\ouput.MP4");
            int c;

            while ((c = in.read()) != -1) {
                out.write(c);
            }
        }
        catch(IOException e) {
            System.out.println("There is IOException!");
        }
        finally {
            if (in != null) {
                in.close();
            }
            if (out != null) {
                out.close();
            }
        }

    }

}
```

## Classes designed to handle Character Streams in Java

![alt text](https://harmash.com/tutorials/java/files-io/6ffe515d-44f1-4d56-abfb-c4f3eeea9bdd_pic_9.PNG)
The two most important classes for dealing with Character Streams are the **FileInputStream** class and the **FileOutputStream** class.

## Classes

In the following table, we have listed some Byte Streams classes that are used to read from files.\
Read :\
https://harmash.com/tutorials/java/files-io \
Write : \
https://harmash.com/tutorials/java/files-io

## Handling folders/files in java

The File class is set up to handle files and directories.
There is no special class to handle folders because folders are empty files that can contain other files and folders.

https://harmash.com/tutorials/java/files-io/file
