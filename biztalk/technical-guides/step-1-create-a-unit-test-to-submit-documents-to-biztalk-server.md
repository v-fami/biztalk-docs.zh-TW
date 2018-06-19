---
title: 步驟 1： 建立單元測試，提交至 BizTalk Server 文件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 688b14e4-bb16-4d12-86b8-37b8b6808472
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8016bc237b55c2404a21c91e2e68d78fdd21bcf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302694"
---
# <a name="step-1-create-a-unit-test-to-submit-documents-to-biztalk-server"></a>步驟 1： 建立單元測試，提交至 BizTalk Server 文件
電腦的應用程式伺服器，例如 BizTalk Server 專為執行特定工作，代表使用者。 這些工作都會起始為以符合應用程式伺服器了解，了解應用程式伺服器的通訊協定透過標準的訊息傳送至應用程式伺服器的用戶端要求。 比方說，用戶端可能會起始處理的電子郵件透過 SMTP 通訊協定的電子郵件伺服器傳送網際網路電子郵件訊息。 同樣地，web 伺服器處理用戶端 HTML 或 ASP 要求，資料庫伺服器處理的 SQL 用戶端要求，而且 BizTalk Server 可以處理用戶端符合使用許多業界標準通訊協定的多個產業訊息標準格式化的訊息。 應用程式伺服器的工作負載容量通常會測量在指定的時段內可以處理應用程式伺服器的訊息數目。 BizTalk Server 的工作負載容量同樣的時間，例如忙碌 workday 或甚至是長測量為 「 每秒接收的文件 」、 「 每秒處理的文件 」 和/或 「 每秒完成的協調流程 」 的平均數目工作週。 Visual Studio 2010 負載測試功能，可以模擬多達數百個使用者同時存取伺服器應用程式的負載設定檔。 這個負載測試功能提供即時的度量資訊。 選取的關鍵效能指標，以及供未來分析資料庫中儲存這些度量的能力。 此文件描述使用 Visual Studio 測試專案，以進行負載測試 BizTalk Server 應用程式，包括如何建立單元測試時，如何建立負載測試，以及如何設定負載測試來擷取效能計數器資料所需判斷最大持續輸送量 (MST) 的 BizTalk Server 應用程式。  
  
## <a name="creating-a-visual-studio-unit-test-to-submit-documents-to-biztalk-server"></a>建立 Visual Studio 單元測試，以提交至 BizTalk Server 文件  
 Visual Studio 單元測試參考[Microsoft.VisualStudio.TestTools.UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID=132293) 命名空間提供數個類別，提供針對單元測試的支援。 特別重要， [UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID = 132293) 命名空間包含[Microsoft.VisualStudio.TestTools.UnitTesting.TestContext](http://go.microsoft.com/fwlink/?LinkID=208233) (http://go.microsoft.com/fwlink/?LinkID = 208233) 來儲存資訊供單元測試的類別和[Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute](http://go.microsoft.com/fwlink/?LinkID=208235) (http://go.microsoft.com/fwlink/?LinkID = 208235) 類別用來定義測試方法。 基於負載測試 BizTalk Server 的詳細資訊，測試方法應指定要載入的訊息和訊息應該傳送到端點/URL。 建立對應的 BizTalk 接收位置時，BizTalk Server 訊息進入點時，將會再服務端點 URL。  
  
 為了說明起見，本主題中的範例程式碼說明測試方法會運用[System.ServiceModel.ChannelFactory(TChannel)](http://go.microsoft.com/fwlink/?LinkId=208238) (http://go.microsoft.com/fwlink/?LinkID = 208238) 類別來傳送訊息至服務端點使用 WCF net.tcp 端點，且會監視由 BizTalk Wcf-custom 接收配接器。 應用程式組態檔 (app.config) 的測試專案中定義的測試訊息的服務端點。  
  
 如需有關 Visual Studio 單元測試，請參閱[單元測試的結構](http://go.microsoft.com/fwlink/?LinkID=208232)(http://go.microsoft.com/fwlink/?LinkID=208232)。  
  
 使用單元測試來提交到一或多個 BizTalk Server 電腦的文件建立測試專案，請遵循下列各節中的步驟。 已完成這些步驟使用 Visual Studio 2010 Ultimate Edition。  
  
### <a name="set-visual-studio-2010-test-project-options"></a>設定 Visual Studio 2010 測試專案選項  
  
1.  啟動 Visual Studio 2010 Ultimate edition。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Visual Studio 2010** ，然後按一下  **Microsoft Visual Studio 2010**。  
  
2.  在 Visual Studio 2010 中，按一下 **工具**，然後按一下 **選項**顯示**選項** 對話方塊。  
  
3.  按一下以展開**測試工具**，然後按一下 **測試專案**以顯示選項來建立新的測試專案。  
  
4.  設定**預設測試專案語言：** 至**Visual C# 測試專案**。  
  
5.  下方的選項**選取的檔案，將會依預設加入至每個新的測試專案：** 選取**Visual C# 測試專案**，並取消核取 所有測試類型的 Visual C# 中的測試專案除外**單元測試**。  
  
6.  按一下 **[確定]** 關閉 **[選項]** 對話方塊。  
  
### <a name="create-a-new-visual-studio-2010-solution-with-a-test-project"></a>建立新的 Visual Studio 2010 方案的測試專案  
  
1.  建立資料夾**C:\Projects** Visual Studio 2010 Ultimate 的電腦上。  
  
2.  Visual Studio 2010 中按一下**檔案**，指向**新增**，然後按一下**專案**顯示**新專案** 對話方塊。  
  
3.  在下**已安裝的範本**按一下以展開**Visual C#**，然後按一下**測試**。  
  
4.  在底部**新專案**對話方塊中指定下列選項：  
  
    -   **名稱：**  
         **BTSLoad**  
  
    -   **位置：**  
         **C:\Projects\\**  
  
    -   **解決方案名稱：**  
         **負載測試**  
  
5.  請確認選項**為方案建立目錄**已核取，然後按一下 **確定**。  
  
6.  將資料夾加入 BTSLoad 專案;這個資料夾將包含測試訊息至提交至 BizTalk Server。 在 [方案總管] 中，以滑鼠右鍵按一下 BTSLoad 專案，指向**新增**，然後按一下**新資料夾**。 反白顯示文字的資料夾圖示**NewFolder1** BTSLoad 專案類型底下會出現**TestMessages**變更反白顯示的文字，然後按**Enter**金鑰若要建立資料夾 C:\Projects\LoadTest\BTSLoad\TestMessages。  
  
### <a name="update-the-code-in-the-test-project-and-add-an-application-configuration-file-to-the-test-project"></a>更新測試專案中的程式碼並將應用程式組態檔加入至測試專案  
  
1.  在 [方案總管] 中按一下以選取**UnitTest1.cs**和現有的程式碼取代下列範例程式碼清單：  
  
    ```csharp  
    #region Using Directives  
    using System;  
    using System.IO;  
    using System.Diagnostics;  
    using System.Text;  
    using System.Configuration;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Xml;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
    #endregion  
  
    namespace Microsoft.BizTalk.Samples  
    {  
        [TestClass]  
        public class BTSLoadTest  
        {  
            #region Constants  
            private const int MaxBufferSize = 2097152;  
            private const string Source = "BTS Load Test";  
            private const string Star = "*";  
            private const string TestMessageFolderParameter = "testMessageFolder";  
            private const string TestMessageFolderDefault = @"C:\Projects\LoadTest\BTSLoad\TestMessages";  
            private const string TestMessageFolderFormat = @"Test Message Folder = {0}";  
            private const string TestXmlDocument = "testxmldocument.xml";  
            #endregion  
  
            #region Private Instance Fields  
            private TestContext testContextInstance;  
            #endregion  
  
            #region Private ThreadStatic Fields  
            [ThreadStatic]  
            private static ChannelFactory<IRequestChannel> channelFactory;  
            [ThreadStatic]  
            private static IRequestChannel channel = null;  
            [ThreadStatic]  
            private static byte[] buffer = null;  
            #endregion  
  
            #region Private Static Fields  
            private static string testMessageFolder = null;  
            #endregion  
  
            #region Public Instance Constructor  
            public BTSLoadTest()  
            {  
            }  
            #endregion  
  
            #region Public Static Constructor  
            static BTSLoadTest()  
            {  
                try  
                {  
                    testMessageFolder = ConfigurationManager.AppSettings[TestMessageFolderParameter];  
                    if (string.IsNullOrEmpty(testMessageFolder))  
                    {  
                        testMessageFolder = TestMessageFolderDefault;  
                    }  
                }  
                catch (Exception ex)  
                {  
                    Trace.WriteLine(ex.Message);  
                    EventLog.WriteEntry(Source, ex.Message, EventLogEntryType.Error);  
                }  
            }  
            #endregion  
  
            #region Public Properties  
            /// <summary>  
            ///Gets or sets the test context which provides  
            ///information about and functionality for the current test run.  
            ///</summary>  
            public TestContext TestContext  
            {  
                get  
                {  
                    return testContextInstance;  
                }  
                set  
                {  
                    testContextInstance = value;  
                }  
            }  
            #endregion  
  
            #region Test Methods  
  
            [TestMethod]  
            public void BTSMessaging()  
            {  
                InvokeBizTalkReceiveLocation("BTSMessagingEP",  
                                               testMessageFolder,  
                                               TestXmlDocument,  
                                               MessageVersion.Default,  
                                               SessionMode.Allowed);  
            }  
  
            [TestMethod]  
            public void BTSMessaging2()  
            {  
                InvokeBizTalkReceiveLocation("BTSMessagingEP2",  
                                               testMessageFolder,  
                                               TestXmlDocument,  
                                               MessageVersion.Default,  
                                               SessionMode.Allowed);  
            }  
  
            [TestMethod]  
            public void BTSOrchestration()  
            {  
                InvokeBizTalkReceiveLocation("BTSOrchestrationEP",  
                                               testMessageFolder,  
                                               TestXmlDocument,  
                                               MessageVersion.Default,  
                                               SessionMode.Allowed);  
            }  
            #endregion  
  
            #region Helper Methods  
            public void InvokeBizTalkReceiveLocation(string endpointConfigurationName,  
                                               string requestMessageFolder,  
                                               string requestMessageName,  
                                               MessageVersion messageVersion,  
                                               SessionMode sessionMode)  
            {  
                XmlTextReader xmlTextReader = null;  
                Message requestMessage = null;  
                Message responseMessage = null;  
  
                try  
                {  
                    if (channel == null || channel.State != CommunicationState.Opened)  
                    {  
                        channelFactory = new ChannelFactory<IRequestChannel>(endpointConfigurationName);  
                        channelFactory.Endpoint.Contract.SessionMode = sessionMode;  
                        channel = channelFactory.CreateChannel();  
                    }  
                    if (buffer == null)  
                    {  
                        string path = Path.Combine(requestMessageFolder, requestMessageName);  
  
                        string message;  
                        using (StreamReader reader = new StreamReader(File.Open(path, FileMode.Open, FileAccess.Read, FileShare.Read)))  
                        {  
                            message = reader.ReadToEnd();  
                        }  
                        buffer = Encoding.UTF8.GetBytes(message);  
                    }  
                    MemoryStream stream = new MemoryStream(buffer);  
                    xmlTextReader = new XmlTextReader(stream);  
                    requestMessage = Message.CreateMessage(messageVersion, Star, xmlTextReader);  
                    TestContext.BeginTimer(requestMessageName);  
                    responseMessage = channel.Request(requestMessage);  
                }  
                catch (FaultException ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                catch (CommunicationException ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                catch (TimeoutException ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                catch (Exception ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                finally  
                {  
                    TestContext.EndTimer(requestMessageName);  
                    CloseObjects(xmlTextReader,  
                                 requestMessage,  
                                 responseMessage);  
                }  
            }  
  
            private void HandleException(Exception ex)  
            {  
                try  
                {  
                    Trace.WriteLine(ex.Message);  
                    EventLog.WriteEntry(Source, ex.Message, EventLogEntryType.Error);  
                }  
                catch (Exception)  
                {  
                }  
            }  
  
            private void CloseObjects(XmlTextReader xmlTextReader,  
                               Message requestMessage,  
                               Message responseMessage)  
            {  
                try  
                {  
                    if (xmlTextReader != null)  
                    {  
                        xmlTextReader.Close();  
                    }  
                    if (requestMessage != null)  
                    {  
                        requestMessage.Close();  
                    }  
                    if (responseMessage != null)  
                    {  
                        responseMessage.Close();  
                    }  
                }  
                catch (Exception)  
                {  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
2.  將應用程式組態檔加入至測試專案：  
  
    1.  在 [方案總管] 中，以滑鼠右鍵按一下 BTSLoad 專案，指向**新增**按一下**新項目**。  
  
    2.  在**加入新項目**對話方塊的 **已安裝的範本**，按一下 **一般**。  
  
    3.  顯示項目清單中按一下以選取**應用程式組態檔**，然後按一下 **新增**。  
  
    4.  在 [方案總管] 中選取 app.config 檔案和 app.config 檔案的內容取代為下面列出的範例程式碼：  
  
        > [!IMPORTANT]  
        >  在此檔案中，定義每個用戶端端點*BizTalk Server 電腦*是 BizTalk Server 將會執行的電腦上載入測試的實際名稱的預留位置。  
  
        ```xml  
  
        <configuration>  
          <system.serviceModel>  
            <!-- Bindings used by client endpoints -->  
            <bindings>  
              <netTcpBinding>  
                <binding name="netTcpBinding" closeTimeout="01:10:00" openTimeout="01:10:00" receiveTimeout="01:10:00" sendTimeout="01:10:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="100" maxBufferPoolSize="1048576" maxBufferSize="10485760" maxConnections="400" maxReceivedMessageSize="10485760">  
                  <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" />  
                  <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false" />  
                  <security mode="None">  
                    <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
                    <message clientCredentialType="Windows" />  
                  </security>  
                </binding>  
              </netTcpBinding>  
            </bindings>  
            <client>  
              <!-- Client endpoints used to exchange messages with WCF Receive Locations -->  
  
              <!-- BTSMessagingEP -->  
              <endpoint address="net.tcp://BizTalk Server Computer:8123/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSMessagingEP" />  
              <endpoint address="net.tcp://BizTalk Server Computer:8123/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSMessagingEP" />  
  
              <!-- BTSOrchestrationEP -->  
              <endpoint address="net.tcp://BizTalk Server Computer:8122/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSOrchestrationEP" />  
            </client>  
          </system.serviceModel>  
          <appSettings>  
            <!-- Folder containing test messages -->  
            <add key="testMessageFolder" value="C:\Projects\LoadTest\BTSLoad\TestMessages" />  
            <add key="ClientSettingsProvider.ServiceUri" value="" />  
          </appSettings>  
        </configuration>  
        ```  
  
    5.  按一下**檔案**在 Visual Studio 2010，然後按一下功能表**全部儲存**。  
  
### <a name="add-a-test-message-to-the-project"></a>將測試訊息加入至專案  
 基於此範例中，BizTalk Server 接收位置和傳送埠會設定為使用通過管線，並不會執行任何文件驗證。 請遵循下列步驟，將測試訊息加入至專案：  
  
1.  啟動 [記事本]。 按一下**啟動**，按一下 [**執行**和型別**記事本**中**執行**] 對話方塊。  
  
2.  將下列文字複製到 [記事本]，並將儲存為"C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml"  
  
    ```  
    <BTSLoadTest xmlns="http://Microsoft.BizTalk.Samples.BTSLoadTest">  
    <MessageText>  
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    </MessageText>  
    </BTSLoadTest>  
    ```  
  
3.  關閉 [記事本]。  
  
> [!IMPORTANT]  
>  這個檔案必須儲存在每個載入的測試代理程式電腦上使用相同的檔案名稱，如果多個負載測試代理程式電腦用於負載測試的相同路徑。  
  
### <a name="add-necessary-references-to-the-project-and-build-the-test-project"></a>新增必要參考加入至專案，並建置測試專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**參考**BTSLoad 專案，然後按一下資料夾**加入參考**。  
  
2.  在 加入參考 對話方塊中，按一下 **.NET**索引標籤，然後使用 CTRL + 按一下鍵盤/滑鼠組合來同時選取 下列.NET 命名空間：  
  
    -   System.Configuration  
  
    -   System.Runtime.Serialization  
  
    -   System.ServiceModel.Channels  
  
    -   System.ServiceModel  
  
    -   System.Web.Extensions  
  
    -   System.Xml  
  
3.  選取命名空間之後按一下**確定**將這些組件新增為 BTSLoad 測試專案的參考。  
  
4.  以滑鼠右鍵按一下**BTSLoad**專案，然後按一下**建置**，將專案編譯成 BTSLoad 組件。