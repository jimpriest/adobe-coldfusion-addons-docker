# Adobe CF2018 Docker + Addons

Trying to get ColdFusion and Addons service running in Docker so I can use cfhtmltopdf.

## Setup

docker-compose up --build

This will run Dockerfile which will install Commandbox and CFConfig and apply default settings.

## Running 

App: http://localhost/
CFAdmin: http://localhost/CFIDE/administrator

CFAdmin login is admin / password.

Notice within the CFAdmin you can successfully verify the PDF Service connection ("OK").

Running the app however returns an error: 

```
coldfusion.document.webkit.PDFgErrorHandler$ServiceManagerConversionException: Error occurred while generating PDF.
	at coldfusion.document.webkit.PDFgErrorHandler.handleConversionError(PDFgErrorHandler.java:190)
	at coldfusion.document.webkit.HttpPDFRequestHandler.requestPDFGeneration(HttpPDFRequestHandler.java:178)
	at coldfusion.tagext.lang.HtmlToPdfTag.processPDFgRequest(HtmlToPdfTag.java:1361)
	at coldfusion.tagext.lang.HtmlToPdfTag.handlePDFgConversionRequest(HtmlToPdfTag.java:1511)
	at coldfusion.tagext.lang.HtmlToPdfTag.convertToPDF(HtmlToPdfTag.java:1448)
	at coldfusion.tagext.lang.HtmlToPdfTag.doEndTag(HtmlToPdfTag.java:1599)
	at cfindex2ecfm41841280.runPage(/app/index.cfm:2)
	at coldfusion.runtime.CfJspPage.invoke(CfJspPage.java:262)
	at coldfusion.tagext.lang.IncludeTag.handlePageInvoke(IncludeTag.java:735)
	at coldfusion.tagext.lang.IncludeTag.doStartTag(IncludeTag.java:565)
	at coldfusion.filter.CfincludeFilter.invoke(CfincludeFilter.java:65)
	at coldfusion.filter.ApplicationFilter.invoke(ApplicationFilter.java:597)
	at coldfusion.filter.RequestMonitorFilter.invoke(RequestMonitorFilter.java:43)
	at coldfusion.filter.MonitoringFilter.invoke(MonitoringFilter.java:40)
	at coldfusion.filter.PathFilter.invoke(PathFilter.java:162)
	at coldfusion.filter.IpFilter.invoke(IpFilter.java:45)
	at coldfusion.filter.LicenseFilter.invoke(LicenseFilter.java:30)
	at coldfusion.filter.ExceptionFilter.invoke(ExceptionFilter.java:96)
	at coldfusion.filter.ClientScopePersistenceFilter.invoke(ClientScopePersistenceFilter.java:28)
	at coldfusion.filter.BrowserFilter.invoke(BrowserFilter.java:38)
	at coldfusion.filter.NoCacheFilter.invoke(NoCacheFilter.java:60)
	at coldfusion.filter.GlobalsFilter.invoke(GlobalsFilter.java:38)
	at coldfusion.filter.DatasourceFilter.invoke(DatasourceFilter.java:22)
	at coldfusion.filter.CachingFilter.invoke(CachingFilter.java:62)
	at coldfusion.CfmServlet.service(CfmServlet.java:226)
	at coldfusion.bootstrap.BootstrapServlet.service(BootstrapServlet.java:311)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:231)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
	at coldfusion.monitor.event.MonitoringServletFilter.doFilter(MonitoringServletFilter.java:46)
	at coldfusion.bootstrap.BootstrapFilter.doFilter(BootstrapFilter.java:47)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
	at coldfusion.inspect.weinre.MobileDeviceDomInspectionFilter.doFilter(MobileDeviceDomInspectionFilter.java:121)
	at coldfusion.bootstrap.BootstrapFilter.doFilter(BootstrapFilter.java:47)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:53)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:202)
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:96)
	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:490)
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:139)
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:92)
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:74)
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:357)
	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:408)
	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:66)
	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:853)
	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1587)
	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)
	at java.base/java.lang.Thread.run(Thread.java:834)
```