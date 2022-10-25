# 考前複習(階段一)
```
package fileProcess;//套件名稱

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class ReadAndParseTxtFile {
   
    public void readTextFile(String filePath) throws IOException {
        FileReader fr 
        	= new FileReader(filePath);//讀取檔案來源路徑
        BufferedReader br
        	= new BufferedReader(fr); //建立BufferedReader的物件br
        
        String temp = null; //
        while( (temp=br.readLine()) != null) {//從檔案中，一次讀取一行，每一行就是一筆顧客資料
        System.out.println(temp);
    }
        //close reader
        if(br != null) {
        br.close();
    }
    }
    
    public static void readTextFile_static(String filePath) throws IOException {
        FileReader fr 
        	= new FileReader(filePath);//讀取檔案來源路徑
        BufferedReader br
          	= new BufferedReader(fr); //建立BufferedReader的物件br
        
        String temp = null; //
        while( (temp=br.readLine()) != null) {//從檔案中，一次讀取一行，每一行就是一筆顧客資料
        System.out.println(temp);
    }
        //close reader
        if(br != null) {
        br.close();
    }
    }
}
```
```
package fileProcessTest;

import java.io.IOException;

import fileProcess.ReadAndParseTxtFile;

public class FileTest {

	public static void main(String[] args) throws IOException {
		ReadAndParseTxtFile obj = new ReadAndParseTxtFile();
		//obj.readTextFile("./data/customer.text");
		
		ReadAndParseTxtFile.readTextFile_static("./data/customer.text");
	}
}
```
# leve2
```
package fileProcessTest;

import java.io.IOException;

import fileProcess.ReadAndParseTxtFile;

public class FileTest {

    public static void main(String[] args) throws IOException {
        
        ReadAndParseTxtFile obj = new ReadAndParseTxtFile();
        obj.readTxtFile("./data/customer.txt");
        
        ReadAndParseTxtFile.readTxtFile_static("./data/customer.txt");

    }

}
```
```
package fileProcess;//套件名稱

import java.io.FileReader;//匯入java.io套件中的 FileReader類別
import java.io.IOException;//匯入java.io套件中的 IOException類別
import java.util.ArrayList;//匯入java.util套件中的 ArrayList類別
import java.io.BufferedReader;//匯入java.io套件中的 BufferedReader類別

public class ReadAndParseTxtFile {

    private ArrayList<String> customer_List 
                                  = new ArrayList<String>();
    private ArrayList<String> customer_ID_List 
                                  = new ArrayList<String>();
    private ArrayList<String> customer_Name_List 
                                  = new ArrayList<String>();
    private ArrayList<String> customer_Address_List 
                                  = new ArrayList<String>();
    private ArrayList<String> customer_Phone_List 
                                  = new ArrayList<String>();
    private ArrayList<String> customer_Email_List 
                                  = new ArrayList<String>();
    
    public void readTxtFile(String filePath) throws IOException {
        //建立FileReader的物件fr，並提供讀取檔案來源路徑為參數
        FileReader fr 
            = new FileReader(filePath);
        
        //建立BufferedReader的物件br，並提供FileReader的物件fr為參數
        BufferedReader br
              = new BufferedReader(fr); //建立BufferedReader的物件br
        
        //宣告一個字串變數temp，儲存從檔案中讀取的一行行的字串行
        String temp = null; 
        String[ ] token; //宣告一個字串陣列，名稱為token
        while( (temp=br.readLine()) != null) {//從檔案中，一次讀取一行，每一行就是一筆顧客資料
            //System.out.println(temp);//列印字串行
            customer_List.add(temp);
            token = temp.split("\t");//對字串temp, 以"\t"為切割依據
            
            //System.out.println(token[0]);//列印出被切割的第1個欄位
            customer_ID_List.add(token[0]);
            //System.out.println(token[1]);//列印出被切割的第2個欄位
            customer_Name_List.add(token[1]);
            //System.out.println(token[2]);//列印出被切割的第3個欄位
            customer_Address_List.add(token[2]);
            //System.out.println(token[3]);//列印出被切割的第4個欄位
            customer_Phone_List.add(token[3]);
            //System.out.println(token[4]);//列印出被切割的第5個欄位
            customer_Email_List.add(token[4]);
            //System.out.println(token.length);//列印出陣列的長度(=被切割的片段數 )
            //System.out.println("-----------------");
        }
            
        //close reader - 關閉BufferedReader br
        if(br != null) {
            br.close();
        }
        
        //列印customer_ID_List ArrayList中的資料
        for(int i = 0; i < customer_ID_List.size(); i++) {
            System.out.println(customer_ID_List.get(i));
        }
        
        System.out.println("----------------------------------------");
        
        //列印customer_Name_List ArrayList中的資料
        for(int i = 0; i < customer_Name_List.size(); i++) {
            System.out.println(customer_Name_List.get(i));
        }
        
    }
    
    public static void readTxtFile_static(String filePath) throws IOException {
        //建立FileReader的物件fr，並提供讀取檔案來源路徑為參數
        FileReader fr 
            = new FileReader(filePath);
        
        //建立BufferedReader的物件br，並提供FileReader的物件fr為參數
        BufferedReader br
              = new BufferedReader(fr); //建立BufferedReader的物件br
        
        //宣告一個字串變數temp，儲存從檔案中讀取的一行行的字串行
        String temp = null; 
        String[ ] token; //宣告一個字串陣列，名稱為token
        while( (temp=br.readLine()) != null) {//從檔案中，一次讀取一行，每一行就是一筆顧客資料
            //System.out.println(temp);//列印字串行
            token = temp.split("\t");//對字串temp, 以"\t"為切割依據
            
            System.out.println(token[0]);//列印出被切割的第1個欄位
            System.out.println(token[1]);//列印出被切割的第2個欄位
            System.out.println(token[2]);//列印出被切割的第3個欄位
            System.out.println(token[3]);//列印出被切割的第4個欄位
            System.out.println(token[4]);//列印出被切割的第5個欄位
            System.out.println(token.length);//列印出陣列的長度(=被切割的片段數 )
            System.out.println("-----------------");
        }
            
        //close reader - 關閉BufferedReader br
        if(br != null) {
            br.close();
        }
    }

}//class結束
```

```
package fileProcessTest;

import java.io.IOException;

import fileProcess.ReadAndParseTxtFile;

public class FileTest {

	public static void main(String[] args) throws IOException {
		ReadAndParseTxtFile obj = new ReadAndParseTxtFile();
		//obj.readTextFile("./data/customer.text");
		
		ReadAndParseTxtFile.readTxtFile_static("./data/customer.txt");
	}
}

```
