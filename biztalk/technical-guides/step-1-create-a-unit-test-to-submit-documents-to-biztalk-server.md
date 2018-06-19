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
# <a name="step-1-create-a-unit-test-to-submit-documents-to-biztalk-server"></a><span data-ttu-id="90052-102">步驟 1： 建立單元測試，提交至 BizTalk Server 文件</span><span class="sxs-lookup"><span data-stu-id="90052-102">Step 1: Create a Unit Test to Submit Documents to BizTalk Server</span></span>
<span data-ttu-id="90052-103">電腦的應用程式伺服器，例如 BizTalk Server 專為執行特定工作，代表使用者。</span><span class="sxs-lookup"><span data-stu-id="90052-103">Computer application servers such as BizTalk Server are designed to perform particular tasks on behalf of users.</span></span> <span data-ttu-id="90052-104">這些工作都會起始為以符合應用程式伺服器了解，了解應用程式伺服器的通訊協定透過標準的訊息傳送至應用程式伺服器的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="90052-104">These tasks are initiated as client requests sent to the application server as messages that conform to a standard that the application server understands, via a protocol that the application server understands.</span></span> <span data-ttu-id="90052-105">比方說，用戶端可能會起始處理的電子郵件透過 SMTP 通訊協定的電子郵件伺服器傳送網際網路電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="90052-105">For example, clients may initiate processing of email by sending internet e-mail messages to an email server via the SMTP protocol.</span></span> <span data-ttu-id="90052-106">同樣地，web 伺服器處理用戶端 HTML 或 ASP 要求，資料庫伺服器處理的 SQL 用戶端要求，而且 BizTalk Server 可以處理用戶端符合使用許多業界標準通訊協定的多個產業訊息標準格式化的訊息。</span><span class="sxs-lookup"><span data-stu-id="90052-106">Likewise, web servers process client HTML or ASP requests, database servers process client SQL requests and BizTalk Server can process client messages formatted in compliance with multiple industry message standards using numerous industry standard protocols.</span></span> <span data-ttu-id="90052-107">應用程式伺服器的工作負載容量通常會測量在指定的時段內可以處理應用程式伺服器的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="90052-107">The workload capacity of an application server is typically measured by the number of messages that the application server can process in a given time period.</span></span> <span data-ttu-id="90052-108">BizTalk Server 的工作負載容量同樣的時間，例如忙碌 workday 或甚至是長測量為 「 每秒接收的文件 」、 「 每秒處理的文件 」 和/或 「 每秒完成的協調流程 」 的平均數目工作週。</span><span class="sxs-lookup"><span data-stu-id="90052-108">The workload capacity of BizTalk Server is likewise measured as the average number of “documents received per second”, “documents processed per second” and/or “orchestrations completed per second” over an extended period of time, such as a busy workday or even a work week.</span></span> <span data-ttu-id="90052-109">Visual Studio 2010 負載測試功能，可以模擬多達數百個使用者同時存取伺服器應用程式的負載設定檔。</span><span class="sxs-lookup"><span data-stu-id="90052-109">Visual Studio 2010 load test functionality can simulate a load profile of up to hundreds of users simultaneously accessing a server application.</span></span> <span data-ttu-id="90052-110">這個負載測試功能提供即時的度量資訊。 選取的關鍵效能指標，以及供未來分析資料庫中儲存這些度量的能力。</span><span class="sxs-lookup"><span data-stu-id="90052-110">This load testing functionality provides real time metrics for selected key performance indicators as well as the ability to store these metrics in a database for future analysis.</span></span> <span data-ttu-id="90052-111">此文件描述使用 Visual Studio 測試專案，以進行負載測試 BizTalk Server 應用程式，包括如何建立單元測試時，如何建立負載測試，以及如何設定負載測試來擷取效能計數器資料所需判斷最大持續輸送量 (MST) 的 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="90052-111">This document desribes the use of Visual Studio Test projects for the purpose of load testing a BizTalk Server application, including how to create unit tests, how to create load tests and how to configure load tests to capture performance counter data required to determine the Maximum Sustainable Throughput (MST) of a BizTalk Server application.</span></span>  
  
## <a name="creating-a-visual-studio-unit-test-to-submit-documents-to-biztalk-server"></a><span data-ttu-id="90052-112">建立 Visual Studio 單元測試，以提交至 BizTalk Server 文件</span><span class="sxs-lookup"><span data-stu-id="90052-112">Creating a Visual Studio Unit Test to Submit Documents to BizTalk Server</span></span>  
 <span data-ttu-id="90052-113">Visual Studio 單元測試參考[Microsoft.VisualStudio.TestTools.UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID=132293) 命名空間提供數個類別，提供針對單元測試的支援。</span><span class="sxs-lookup"><span data-stu-id="90052-113">A Visual Studio Unit test references the [Microsoft.VisualStudio.TestTools.UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID=132293) namespace which supplies several classes that provide support for unit testing.</span></span> <span data-ttu-id="90052-114">特別重要， [UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID = 132293) 命名空間包含[Microsoft.VisualStudio.TestTools.UnitTesting.TestContext](http://go.microsoft.com/fwlink/?LinkID=208233) (http://go.microsoft.com/fwlink/?LinkID = 208233) 來儲存資訊供單元測試的類別和[Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute](http://go.microsoft.com/fwlink/?LinkID=208235) (http://go.microsoft.com/fwlink/?LinkID = 208235) 類別用來定義測試方法。</span><span class="sxs-lookup"><span data-stu-id="90052-114">Of particular importance, the [UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID=132293) namespace includes the [Microsoft.VisualStudio.TestTools.UnitTesting.TestContext](http://go.microsoft.com/fwlink/?LinkID=208233) (http://go.microsoft.com/fwlink/?LinkID=208233) class to store information provided to Unit tests and the [Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute](http://go.microsoft.com/fwlink/?LinkID=208235) (http://go.microsoft.com/fwlink/?LinkID=208235) class is used to define Test methods.</span></span> <span data-ttu-id="90052-115">基於負載測試 BizTalk Server 的詳細資訊，測試方法應指定要載入的訊息和訊息應該傳送到端點/URL。</span><span class="sxs-lookup"><span data-stu-id="90052-115">For purposes of load testing BizTalk Server, Test methods should specify the message to be loaded and the endpoint/URL to which the message should be sent.</span></span> <span data-ttu-id="90052-116">建立對應的 BizTalk 接收位置時，BizTalk Server 訊息進入點時，將會再服務端點 URL。</span><span class="sxs-lookup"><span data-stu-id="90052-116">The endpoint/URL will then serve as the message entry point into BizTalk Server when a corresponding BizTalk receive location is created.</span></span>  
  
 <span data-ttu-id="90052-117">為了說明起見，本主題中的範例程式碼說明測試方法會運用[System.ServiceModel.ChannelFactory(TChannel)](http://go.microsoft.com/fwlink/?LinkId=208238) (http://go.microsoft.com/fwlink/?LinkID = 208238) 類別來傳送訊息至服務端點使用 WCF net.tcp 端點，且會監視由 BizTalk Wcf-custom 接收配接器。</span><span class="sxs-lookup"><span data-stu-id="90052-117">For purposes of illustration, the sample code in this topic describes Test methods which utilize the [System.ServiceModel.ChannelFactory(TChannel)](http://go.microsoft.com/fwlink/?LinkId=208238) (http://go.microsoft.com/fwlink/?LinkID=208238) class to send messages to service endpoints that use the WCF net.tcp endpoint and are monitored by the BizTalk WCF-Custom receive adapter.</span></span> <span data-ttu-id="90052-118">應用程式組態檔 (app.config) 的測試專案中定義的測試訊息的服務端點。</span><span class="sxs-lookup"><span data-stu-id="90052-118">Service endpoints for test messages are defined in the Application Configuration (app.config) file of the Test project.</span></span>  
  
 <span data-ttu-id="90052-119">如需有關 Visual Studio 單元測試，請參閱[單元測試的結構](http://go.microsoft.com/fwlink/?LinkID=208232)(http://go.microsoft.com/fwlink/?LinkID=208232)。</span><span class="sxs-lookup"><span data-stu-id="90052-119">For more information about Visual Studio Unit Tests see [Anatomy of a Unit Test](http://go.microsoft.com/fwlink/?LinkID=208232) (http://go.microsoft.com/fwlink/?LinkID=208232).</span></span>  
  
 <span data-ttu-id="90052-120">使用單元測試來提交到一或多個 BizTalk Server 電腦的文件建立測試專案，請遵循下列各節中的步驟。</span><span class="sxs-lookup"><span data-stu-id="90052-120">Follow the steps in the sections below to create a Test project with a Unit Test to submit documents to one or more BizTalk Server computers.</span></span> <span data-ttu-id="90052-121">已完成這些步驟使用 Visual Studio 2010 Ultimate Edition。</span><span class="sxs-lookup"><span data-stu-id="90052-121">These steps were completed using Visual Studio 2010 Ultimate Edition.</span></span>  
  
### <a name="set-visual-studio-2010-test-project-options"></a><span data-ttu-id="90052-122">設定 Visual Studio 2010 測試專案選項</span><span class="sxs-lookup"><span data-stu-id="90052-122">Set Visual Studio 2010 Test Project Options</span></span>  
  
1.  <span data-ttu-id="90052-123">啟動 Visual Studio 2010 Ultimate edition。</span><span class="sxs-lookup"><span data-stu-id="90052-123">Launch Visual Studio 2010 Ultimate edition.</span></span> <span data-ttu-id="90052-124">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Visual Studio 2010** ，然後按一下  **Microsoft Visual Studio 2010**。</span><span class="sxs-lookup"><span data-stu-id="90052-124">Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2010** and then click **Microsoft Visual Studio 2010**.</span></span>  
  
2.  <span data-ttu-id="90052-125">在 Visual Studio 2010 中，按一下 **工具**，然後按一下 **選項**顯示**選項** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="90052-125">In Visual Studio 2010, click **Tools** and then click **Options** to display the **Options** dialog box.</span></span>  
  
3.  <span data-ttu-id="90052-126">按一下以展開**測試工具**，然後按一下 **測試專案**以顯示選項來建立新的測試專案。</span><span class="sxs-lookup"><span data-stu-id="90052-126">Click to expand **Test Tools** and then click **Test Project** to display options for creation of new test projects.</span></span>  
  
4.  <span data-ttu-id="90052-127">設定**預設測試專案語言：** 至**Visual C# 測試專案**。</span><span class="sxs-lookup"><span data-stu-id="90052-127">Set the **Default test project language:** to **Visual C# test project**.</span></span>  
  
5.  <span data-ttu-id="90052-128">下方的選項**選取的檔案，將會依預設加入至每個新的測試專案：** 選取**Visual C# 測試專案**，並取消核取 所有測試類型的 Visual C# 中的測試專案除外**單元測試**。</span><span class="sxs-lookup"><span data-stu-id="90052-128">Under the option to **Select the files that will be added to each new test project, by default:** select **Visual C# test project**, and uncheck all of the test types for Visual C# test projects except for **Unit Test**.</span></span>  
  
6.  <span data-ttu-id="90052-129">按一下 **[確定]** 關閉 **[選項]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="90052-129">Click **OK** to close the **Options** dialog box.</span></span>  
  
### <a name="create-a-new-visual-studio-2010-solution-with-a-test-project"></a><span data-ttu-id="90052-130">建立新的 Visual Studio 2010 方案的測試專案</span><span class="sxs-lookup"><span data-stu-id="90052-130">Create a new Visual Studio 2010 Solution with a Test Project</span></span>  
  
1.  <span data-ttu-id="90052-131">建立資料夾**C:\Projects** Visual Studio 2010 Ultimate 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="90052-131">Create the folder **C:\Projects** on the Visual Studio 2010 Ultimate computer.</span></span>  
  
2.  <span data-ttu-id="90052-132">Visual Studio 2010 中按一下**檔案**，指向**新增**，然後按一下**專案**顯示**新專案** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="90052-132">In Visual Studio 2010 click **File**, point to **New**, and click **Project** to display the **New Project** dialog box.</span></span>  
  
3.  <span data-ttu-id="90052-133">在下**已安裝的範本**按一下以展開**Visual C#**，然後按一下**測試**。</span><span class="sxs-lookup"><span data-stu-id="90052-133">Under **Installed Templates** click to expand **Visual C#**, and click **Test**.</span></span>  
  
4.  <span data-ttu-id="90052-134">在底部**新專案**對話方塊中指定下列選項：</span><span class="sxs-lookup"><span data-stu-id="90052-134">At the bottom of the **New Project** dialog box specify the following options:</span></span>  
  
    -   <span data-ttu-id="90052-135">**名稱：**</span><span class="sxs-lookup"><span data-stu-id="90052-135">**Name:**</span></span>  
         <span data-ttu-id="90052-136">**BTSLoad**</span><span class="sxs-lookup"><span data-stu-id="90052-136">**BTSLoad**</span></span>  
  
    -   <span data-ttu-id="90052-137">**位置：**</span><span class="sxs-lookup"><span data-stu-id="90052-137">**Location:**</span></span>  
         <span data-ttu-id="90052-138">**C:\Projects\\**</span><span class="sxs-lookup"><span data-stu-id="90052-138">**C:\Projects\\**</span></span>  
  
    -   <span data-ttu-id="90052-139">**解決方案名稱：**</span><span class="sxs-lookup"><span data-stu-id="90052-139">**Solution name:**</span></span>  
         <span data-ttu-id="90052-140">**負載測試**</span><span class="sxs-lookup"><span data-stu-id="90052-140">**LoadTest**</span></span>  
  
5.  <span data-ttu-id="90052-141">請確認選項**為方案建立目錄**已核取，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="90052-141">Ensure that the option to **Create directory for solution** is checked and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="90052-142">將資料夾加入 BTSLoad 專案;這個資料夾將包含測試訊息至提交至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="90052-142">Add a folder to the BTSLoad project; this folder will contain test messages to be submitted to BizTalk Server.</span></span> <span data-ttu-id="90052-143">在 [方案總管] 中，以滑鼠右鍵按一下 BTSLoad 專案，指向**新增**，然後按一下**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="90052-143">In Solution Explorer, right-click the BTSLoad project, point to **Add**, and click **New Folder**.</span></span> <span data-ttu-id="90052-144">反白顯示文字的資料夾圖示**NewFolder1** BTSLoad 專案類型底下會出現**TestMessages**變更反白顯示的文字，然後按**Enter**金鑰若要建立資料夾 C:\Projects\LoadTest\BTSLoad\TestMessages。</span><span class="sxs-lookup"><span data-stu-id="90052-144">A folder icon with the highlighted text **NewFolder1** will appear under the BTSLoad project, type **TestMessages** to change the highlighted text and press the **Enter** key to create the folder C:\Projects\LoadTest\BTSLoad\TestMessages.</span></span>  
  
### <a name="update-the-code-in-the-test-project-and-add-an-application-configuration-file-to-the-test-project"></a><span data-ttu-id="90052-145">更新測試專案中的程式碼並將應用程式組態檔加入至測試專案</span><span class="sxs-lookup"><span data-stu-id="90052-145">Update the Code in the Test Project and add an Application Configuration File to the Test Project</span></span>  
  
1.  <span data-ttu-id="90052-146">在 [方案總管] 中按一下以選取**UnitTest1.cs**和現有的程式碼取代下列範例程式碼清單：</span><span class="sxs-lookup"><span data-stu-id="90052-146">In Solution Explorer click to select **UnitTest1.cs** and replace the existing code with the following sample code listing:</span></span>  
  
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
  
2.  <span data-ttu-id="90052-147">將應用程式組態檔加入至測試專案：</span><span class="sxs-lookup"><span data-stu-id="90052-147">Add an Application Configuration file to the Test project:</span></span>  
  
    1.  <span data-ttu-id="90052-148">在 [方案總管] 中，以滑鼠右鍵按一下 BTSLoad 專案，指向**新增**按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="90052-148">In Solution Explorer, right-click the BTSLoad project, point to **Add** and click **New item**.</span></span>  
  
    2.  <span data-ttu-id="90052-149">在**加入新項目**對話方塊的 **已安裝的範本**，按一下 **一般**。</span><span class="sxs-lookup"><span data-stu-id="90052-149">In the **Add New Item** dialog box, under **Installed Templates**, click **General**.</span></span>  
  
    3.  <span data-ttu-id="90052-150">顯示項目清單中按一下以選取**應用程式組態檔**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="90052-150">In the list of items that are displayed click to select **Application Configuration File** and then click **Add**.</span></span>  
  
    4.  <span data-ttu-id="90052-151">在 [方案總管] 中選取 app.config 檔案和 app.config 檔案的內容取代為下面列出的範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="90052-151">In Solution Explorer select the app.config file and replace the contents of the app.config file with the sample code listing below:</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="90052-152">在此檔案中，定義每個用戶端端點*BizTalk Server 電腦*是 BizTalk Server 將會執行的電腦上載入測試的實際名稱的預留位置。</span><span class="sxs-lookup"><span data-stu-id="90052-152">For each client endpoint defined in this file, *BizTalk Server Computer* is a placeholder for the actual name of the BizTalk Server computer(s) that you will perform load testing against.</span></span>  
  
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
  
    5.  <span data-ttu-id="90052-153">按一下**檔案**在 Visual Studio 2010，然後按一下功能表**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="90052-153">Click the **File** menu in Visual Studio 2010 and then click **Save All**.</span></span>  
  
### <a name="add-a-test-message-to-the-project"></a><span data-ttu-id="90052-154">將測試訊息加入至專案</span><span class="sxs-lookup"><span data-stu-id="90052-154">Add a Test Message to the Project</span></span>  
 <span data-ttu-id="90052-155">基於此範例中，BizTalk Server 接收位置和傳送埠會設定為使用通過管線，並不會執行任何文件驗證。</span><span class="sxs-lookup"><span data-stu-id="90052-155">For purposes of this example, BizTalk Server receive location(s) and send port(s) will be configured to use pass through pipelines and will not perform any document validation.</span></span> <span data-ttu-id="90052-156">請遵循下列步驟，將測試訊息加入至專案：</span><span class="sxs-lookup"><span data-stu-id="90052-156">Follow these steps to add a test message to the project:</span></span>  
  
1.  <span data-ttu-id="90052-157">啟動 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="90052-157">Launch Notepad.</span></span> <span data-ttu-id="90052-158">按一下**啟動**，按一下 [**執行**和型別**記事本**中**執行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="90052-158">Click **Start**, click **Run** and type **Notepad** in the **Run** dialog box.</span></span>  
  
2.  <span data-ttu-id="90052-159">將下列文字複製到 [記事本]，並將儲存為"C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml"</span><span class="sxs-lookup"><span data-stu-id="90052-159">Copy the following text into Notepad and save as “C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml”</span></span>  
  
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
  
3.  <span data-ttu-id="90052-160">關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="90052-160">Close Notepad.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="90052-161">這個檔案必須儲存在每個載入的測試代理程式電腦上使用相同的檔案名稱，如果多個負載測試代理程式電腦用於負載測試的相同路徑。</span><span class="sxs-lookup"><span data-stu-id="90052-161">This file will need to be saved to the same path using the same file name on every Load Test Agent computer if multiple Load Test Agent computers are used for load testing.</span></span>  
  
### <a name="add-necessary-references-to-the-project-and-build-the-test-project"></a><span data-ttu-id="90052-162">新增必要參考加入至專案，並建置測試專案</span><span class="sxs-lookup"><span data-stu-id="90052-162">Add Necessary References to the Project and Build the Test Project</span></span>  
  
1.  <span data-ttu-id="90052-163">在 [方案總管] 中，以滑鼠右鍵按一下**參考**BTSLoad 專案，然後按一下資料夾**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="90052-163">In Solution Explorer, right-click the **References** folder for the BTSLoad project and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="90052-164">在 加入參考 對話方塊中，按一下 **.NET**索引標籤，然後使用 CTRL + 按一下鍵盤/滑鼠組合來同時選取 下列.NET 命名空間：</span><span class="sxs-lookup"><span data-stu-id="90052-164">In the Add Reference dialog box, click the **.NET** tab and use the CTRL+Click keyboard/mouse combination to simultaneously select the following .NET namespaces:</span></span>  
  
    -   <span data-ttu-id="90052-165">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="90052-165">System.Configuration</span></span>  
  
    -   <span data-ttu-id="90052-166">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="90052-166">System.Runtime.Serialization</span></span>  
  
    -   <span data-ttu-id="90052-167">System.ServiceModel.Channels</span><span class="sxs-lookup"><span data-stu-id="90052-167">System.ServiceModel.Channels</span></span>  
  
    -   <span data-ttu-id="90052-168">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="90052-168">System.ServiceModel</span></span>  
  
    -   <span data-ttu-id="90052-169">System.Web.Extensions</span><span class="sxs-lookup"><span data-stu-id="90052-169">System.Web.Extensions</span></span>  
  
    -   <span data-ttu-id="90052-170">System.Xml</span><span class="sxs-lookup"><span data-stu-id="90052-170">System.Xml</span></span>  
  
3.  <span data-ttu-id="90052-171">選取命名空間之後按一下**確定**將這些組件新增為 BTSLoad 測試專案的參考。</span><span class="sxs-lookup"><span data-stu-id="90052-171">After selecting the namespaces click **OK** to add these assemblies as references to the BTSLoad Test project.</span></span>  
  
4.  <span data-ttu-id="90052-172">以滑鼠右鍵按一下**BTSLoad**專案，然後按一下**建置**，將專案編譯成 BTSLoad 組件。</span><span class="sxs-lookup"><span data-stu-id="90052-172">Right click the **BTSLoad** project and then click **Build** to compile the project into the BTSLoad assembly.</span></span>