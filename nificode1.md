<processor name="GetHTTP">
    <type>org.apache.nifi.processors.standard.GetHTTP</type>
    <properties>
        <property name="URL">${stock_data_url}</property>
        <property name="Authentication Method">None</property>
    </properties>
    <description />
</processor>


<processor name="ExtractText">
    <type>org.apache.nifi.processors.standard.ExtractText</type>
    <properties>
        <property name="Search Attribute">http.status</property>
        <property name="Search Value">200</property>
        <property name="Attribute To Extract">content</property>
    </properties>
    <description />
</processor>


<processor name="ConvertRecord">
    <type>org.apache.nifi.processors.record.ConvertRecord</type>
    <properties>
        <property name="Record Reader">JsonTreeReader</property>
        <property name="Record Writer">ParquetRecordWriter</property>
    </properties>
    <description />
</processor>


<processor name="PutHDFS">
    <type>org.apache.nifi.processors.hadoop.PutHDFS</type>
    <properties>
        <property name="Directory">/user/nifi/stock_data</property>
        <property name="File Name">${now():format('yyyy-MM-dd')}_stocks.parquet</property>
    </properties>
    <description />
</processor>


Write code for NiFi to read stocks and store in apache iceberg
Here is an example of a NiFi flow that reads stock data and stores it in Apache Iceberg. Please note that the specifics of the implementation will depend on the data source, data format, and specific requirements of your use case.

GetHTTP Processor:
php
Copy code
<processor name="GetHTTP">
    <type>org.apache.nifi.processors.standard.GetHTTP</type>
    <properties>
        <property name="URL">${stock_data_url}</property>
        <property name="Authentication Method">None</property>
    </properties>
    <description />
</processor>
ExtractText Processor:
php
Copy code
<processor name="ExtractText">
    <type>org.apache.nifi.processors.standard.ExtractText</type>
    <properties>
        <property name="Search Attribute">http.status</property>
        <property name="Search Value">200</property>
        <property name="Attribute To Extract">content</property>
    </properties>
    <description />
</processor>
ConvertRecord Processor:
php
Copy code
<processor name="ConvertRecord">
    <type>org.apache.nifi.processors.record.ConvertRecord</type>
    <properties>
        <property name="Record Reader">JsonTreeReader</property>
        <property name="Record Writer">ParquetRecordWriter</property>
    </properties>
    <description />
</processor>
PutHDFS Processor:
php
Copy code
<processor name="PutHDFS">
    <type>org.apache.nifi.processors.hadoop.PutHDFS</type>
    <properties>
        <property name="Directory">/user/nifi/stock_data</property>
        <property name="File Name">${now():format('yyyy-MM-dd')}_stocks.parquet</property>
    </properties>
    <description />
</processor>
Apache Iceberg:
Apache Iceberg can be used to sink the data stored in HDFS into the data lake. You can use the Iceberg.storage.file-base-dir property in the Iceberg configuration file to specify the location of the data lake in HDFS, e.g. /user/nifi/data_lake.
Note: The above code is just a basic example and may need to be modified depending on your specific requirements and constraints.
