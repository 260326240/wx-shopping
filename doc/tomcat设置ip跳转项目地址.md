## 设置 访问服务器ip跳转到项目地址方法：
  在tomcat中的目录下的conf/server.xml中找到如下代码段

    <Connector port="80" protocol="HTTP/1.1"
       connectionTimeout="20000"
       redirectPort="8443" />
	port:8080 --> 80
  默认打开网址是访问网址的80端口。
  
  添加代码段

    <Context path="" docBase="项目名称" debug="0" reloadable="true" />
  在项目名称中填入内容即可。
  该代码段放置<Host>代码段</Host>中

1. 在xshell界面修改tomcat的server.xml，导致server.xml对应编码不一致报错  
1. 解决方法：复制新的server.xml到vscode或者编辑器修改，修改好了再上传到服务器


### 出现问题如下：
----------

    
    org.apache.tomcat.util.digester.Digester.fatalError Parse Fatal Error at line 1 column 36: Element type "xml" must be followed by either attribute specifications, ">" or "/>".
     org.xml.sax.SAXParseException; systemId: file:/home/apache-tomcat-8.0.53/conf/server.xml; lineNumber: 1; columnNumber: 36; Element type "xml" must be followed by either attribute specifications, ">" or "/>".
    	at com.sun.org.apache.xerces.internal.util.ErrorHandlerWrapper.createSAXParseException(ErrorHandlerWrapper.java:203)
    	at com.sun.org.apache.xerces.internal.util.ErrorHandlerWrapper.fatalError(ErrorHandlerWrapper.java:177)
    	at com.sun.org.apache.xerces.internal.impl.XMLErrorReporter.reportError(XMLErrorReporter.java:400)
    	at com.sun.org.apache.xerces.internal.impl.XMLErrorReporter.reportError(XMLErrorReporter.java:327)
    	at com.sun.org.apache.xerces.internal.impl.XMLScanner.reportFatalError(XMLScanner.java:1472)
    	at com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.seekCloseOfStartTag(XMLDocumentFragmentScannerImpl.java:1394)
    	at com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.scanStartElement(XMLDocumentFragmentScannerImpl.java:1324)
    	at com.sun.org.apache.xerces.internal.impl.XMLDocumentScannerImpl$ContentDriver.scanRootElementHook(XMLDocumentScannerImpl.java:1289)
    	at com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl$FragmentContentDriver.next(XMLDocumentFragmentScannerImpl.java:3132)
    	at com.sun.org.apache.xerces.internal.impl.XMLDocumentScannerImpl$PrologDriver.next(XMLDocumentScannerImpl.java:852)
    	at com.sun.org.apache.xerces.internal.impl.XMLDocumentScannerImpl.next(XMLDocumentScannerImpl.java:602)
    	at com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.scanDocument(XMLDocumentFragmentScannerImpl.java:505)
    	at com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:842)
    	at com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:771)
    	at com.sun.org.apache.xerces.internal.parsers.XMLParser.parse(XMLParser.java:141)
    	at com.sun.org.apache.xerces.internal.parsers.AbstractSAXParser.parse(AbstractSAXParser.java:1213)
    	at com.sun.org.apache.xerces.internal.jaxp.SAXParserImpl$JAXPSAXParser.parse(SAXParserImpl.java:643)
    	at org.apache.tomcat.util.digester.Digester.parse(Digester.java:1449)
    	at org.apache.catalina.startup.Catalina.load(Catalina.java:564)
    	at org.apache.catalina.startup.Catalina.load(Catalina.java:615)
    	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    	at java.lang.reflect.Method.invoke(Method.java:498)
    	at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:308)
    	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:482)
    
    21-Nov-2018 12:22:15.542 WARNING [main] org.apache.catalina.startup.Catalina.load Catalina.start using conf/server.xml: Element type "xml" must be followed by either attribute specifications, ">" or "/>".
    21-Nov-2018 12:22:15.542 SEVERE [main] org.apache.catalina.startup.Catalina.start Cannot start server. Server instance is not configured.