# dcsv
Dakside CSV is a light weight library for CSV data manipulation.

## Introduction

Dakside.CSV is a lightweight yet powerful library for process CSV file. Main features of dCSV are:

1. Thread-safe of write & read CSV file from/to streams, readers, and files.
2. Fast learning curve (CSV library is very easy to use).
3. Small size (7KB in total)

## Examples

Reading CSV data is very easy:

``` java
import dakside.csv.*;

public class Example2 {
  public static void main(String[] args) {
    CSVFile csv = CSVFileReader.parseFile("/home/someone/sample.csv");
  }
} 
```

Writing content to CSV file:

``` java
import dakside.csv.CSVFile;
import dakside.csv.CSVFileWriter;
import java.util.Date;

public class ExampleSimple {

  public static void main(String[] args) {
    CSVFile csvData = new CSVFile();
    //add some data
    csvData.newLine().add("Name").add("Salary").add("Birthday"); //line 1
    csvData.newLine().add("Boo").add(4300).add(new Date(86, 4, 23)); //line 2
    csvData.newLine().add("Joe").add(6800.5).add(new Date(84, 9, 27)); //line 3

    //Create a writer to write CSV data
    CSVFileWriter writer = new CSVFileWriter("/home/someone/employees.csv");

    //Write csvData to file
    writer.writeFile(csvData);

    //Close file (auto save)
    writer.close();
  }
} 
```

and here is the results.

```File: employees.csv

Name,Salary,Birthday
Boo,4300,Fri May 23 00:00:00 SGT 1986
Joe,6800.5,Sat Oct 27 00:00:00 SGT 1984 
```

