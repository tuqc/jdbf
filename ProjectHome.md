## jdbf introduction ##
A common java reader writer library for the DBF database file.
The original http://code.google.com/p/java-dbf/ will be removed.
It's very easy to use.

## jdbf example ##
**e.g. Write a DBF:
```
   public static void main(String args[])
        throws Exception
    {
        JDBField[] fields = {
            new JDBField("ID", 'C', 8, 0),
            new JDBField("Name", 'C', 32, 0),
            new JDBField("TestN", 'N', 20, 0), //第三个参数值一定不大于20
            new JDBField("TestF", 'F', 20, 6), //F类型与N类型同,且第四个参数值有小数位数，否则会截短
            new JDBField("TestD", 'D', 8, 0)
        };
        //DBFReader dbfreader = new DBFReader("E:\\hexiong\\work\\project\\book2.dbf");
        DBFWriter dbfwriter = new DBFWriter("./testwrite.dbf", fields);

        Object[][] records = {
            {"1", "hexiong", new Integer(500), new Double(500.123), new Date() },
            {"2", "hefang", new Integer(600), new Double(600.234), new Date() },
            {"3", "heqiang", new Integer(700), new Double(700.456), new Date() }
        };

        for (int i=0; i<records.length; i++){
          dbfwriter.addRecord(records[i]);
        }
        dbfwriter.close();
        System.out.println("testwrite.dbf write finished.......");
    }
```**

**e.g. Read a dbf:
```
    public static void main(String args[])
        throws Exception
    {
        //DBFReader dbfreader = new DBFReader((new URL("http://www.svcon.com/us48st.dbf")).openStream());
        //DBFReader dbfreader = new DBFReader("F:\\work\\book2.dbf");
        DBFReader dbfreader = new DBFReader("./book2.dbf");
        //DBFReader dbfreader = new DBFReader("E:\\hexiongshare\\test.dbf");
        int i;
        for (i=0; i<dbfreader.getFieldCount(); i++) {
          System.out.print(dbfreader.getField(i).getName()+"  ");
        }
        System.out.print("\n");
        for(i = 0; dbfreader.hasNextRecord(); i++)
        {
            Object aobj[] = dbfreader.nextRecord(Charset.forName("GBK"));
            for (int j=0; j<aobj.length; j++)
              System.out.print(aobj[j]+"  |  ");
            System.out.print("\n");
        }

        System.out.println("Total Count: " + i);
    }
```**

## contact with me ##
Any issues, please contact with me. hexiong AT gmail.com.

The library and source code download is available. The latest version is jdbf-1.1.



## donation ##
Any donation is appreciated:  Donation: http://www138.com/donation.htm