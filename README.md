# java
The note of java learning exception.

//IOException: 发生 I/O 错误时引发的异常。
//IOException是使用流、文件和目录访问信息时引发的异常的基类。当你要使用流,文件,目录访问时需要使用,比如读取一段输入流发生异常,写入一个文件发生异常等等
//在应用时try，在方法中throws IOException

package io.filewriter;  

import java.io.FileWriter;  
import java.io.IOException;  

public class IOExceptionDemo {  

    private static final String LINE_SRPATATOR = System.getProperty("line.separator");  

    public static void main(String[] args)  {  

        FileWriter fw=null;  


        try {  
            fw=new FileWriter("k:\\demo.txt");  

        fw.write("xixi");  
        fw.write(LINE_SRPATATOR);  
        fw.write("aaaa");  
        } catch (IOException e) {  
            System.out.println(e.toString());  
        }  


        /* 
         * 关闭流 关闭资源 在关闭前会调用flush刷新缓冲中的数据到目的地 
         */  
        finally {  
            if(fw!=null)//防止空指针异常  
             try {  
                fw.close();  
            } catch (IOException e) {  
                throw new RuntimeException("关闭失败");  
            }  
        }  



    }  

}  
