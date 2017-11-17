---
title: "步驟 17： 建立 WSClient 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WSClient application
- message enrichment tutorial, WSClient application
- creating, WSClient application
ms.assetid: 2849cd4c-30d0-47ab-8161-fab379d5a548
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8028688f918854d8251f7b059c76642800961088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-17-create-the-wsclient-application"></a><span data-ttu-id="51ce8-102">步驟 17： 建立 WSClient 應用程式</span><span class="sxs-lookup"><span data-stu-id="51ce8-102">Step 17: Create the WSClient Application</span></span>
<span data-ttu-id="51ce8-103">WSClient.exe （Web 服務用戶端） 是主控台應用程式，以撰寫[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]，說明如何將資料傳送至協調流程發佈為 Web 服務，在先前的步驟。</span><span class="sxs-lookup"><span data-stu-id="51ce8-103">WSClient.exe (Web service client) is a console application written in [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] that illustrates how to send data to the orchestration that you published as a Web service in the previous steps.</span></span> <span data-ttu-id="51ce8-104">WSClient 應用程式會接受四個輸入參數順序： 病患名字、 中間名可姓氏，與社會安全號碼，分別。</span><span class="sxs-lookup"><span data-stu-id="51ce8-104">The WSClient application accepts four input parameters in order: patient first name, middle name, last name, and social security number, respectively.</span></span> <span data-ttu-id="51ce8-105">若要將病患資訊傳送至您的 Web 服務，使用下列命令列語法：</span><span class="sxs-lookup"><span data-stu-id="51ce8-105">To send patient information to your Web service, use the following command line syntax:</span></span>  
  
```  
wsclient john henry smith 123456789  
```  
  
### <a name="to-create-the-wsclient-application"></a><span data-ttu-id="51ce8-106">若要建立 WSClient 應用程式</span><span class="sxs-lookup"><span data-stu-id="51ce8-106">To create the WSClient application</span></span>  
  
1.  <span data-ttu-id="51ce8-107">在 方案總管 中，以滑鼠右鍵按一下**方案 'BTAHL7V22Common'**，按一下 **新增**，然後按一下 **新專案**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-107">In Solution Explorer, right-click **Solution 'BTAHL7V22Common'**, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="51ce8-108">在**加入新的專案**對話方塊中，於**專案類型** 窗格中，按一下  **Visual C#**和**範本** 窗格中，按一下**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-108">In the **Add New Project** dialog box, in the **Project Types** pane, click **Visual C#** and in the **Templates** pane, click **Console Application**.</span></span>  
  
3.  <span data-ttu-id="51ce8-109">在**名稱**欄位中，輸入**WSClient**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-109">In the **Name** field, type **WSClient**.</span></span> <span data-ttu-id="51ce8-110">在**位置**欄位中，瀏覽至  **\<*磁碟機*>: \Tutorial**，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-110">In the **Location** field, browse to **\<*drive*>:\Tutorial**, and then click **OK**.</span></span> <span data-ttu-id="51ce8-111">方案總管 樹狀結構中，加入 WSClient 並在 Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="51ce8-111">Solution Explorer adds WSClient to the tree, and the Program.cs file appears.</span></span>  
  
4.  <span data-ttu-id="51ce8-112">在 方案總管 中，以滑鼠右鍵按一下**WSClient**，然後按一下 **加入 Web 參考**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-112">In Solution Explorer, right-click **WSClient**, and then click **Add Web Reference**.</span></span>  
  
5.  <span data-ttu-id="51ce8-113">在 [加入 Web 參考] 對話方塊中，按一下**本機電腦上的 Web 服務**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-113">In the Add Web Reference dialog box, click **Web services on the local machine**.</span></span> <span data-ttu-id="51ce8-114">本機電腦搜尋可用的 Web 服務，並顯示在清單中。</span><span class="sxs-lookup"><span data-stu-id="51ce8-114">The local computer searches for available Web services, and then displays them in a list.</span></span>  
  
6.  <span data-ttu-id="51ce8-115">在本機電腦上的 Web 服務清單中，按一下  **BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**，按一下  **Operation_1**，然後按一下 **加入參考**.</span><span class="sxs-lookup"><span data-stu-id="51ce8-115">In the list of Web Services on the Local Machine, click **BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, click **Operation_1**, and then click **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="51ce8-116">按兩下 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="51ce8-116">Double-click Program.cs.</span></span>  
  
8.  <span data-ttu-id="51ce8-117">下列程式碼複製並貼到 [Program.cs] 視窗：</span><span class="sxs-lookup"><span data-stu-id="51ce8-117">Copy the following code and then paste it into the Program.cs window:</span></span>  
  
    ```  
    using System;  
  
    namespace WSClient  
    {  
       class Class1  
       {  
          [STAThread]  
          static void Main(string[] args)  
          {  
             try   
             {  
                localhost.DoorbellRoot req=new WSClient.localhost.DoorbellRoot();  
                req.FirstName=args[0];  
                req.MiddleName=args[1];  
                req.LastName=args[2];  
                req.SSN=args[3];  
                localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort sp=new WSClient.localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort();  
                sp.Operation_1(req);  
             }  
             catch (Exception ex)  
             {  
                Console.WriteLine(ex.Message);  
             }  
          }  
       }  
    }  
    ```  
  
9. <span data-ttu-id="51ce8-118">在 方案總管 中，以滑鼠右鍵按一下**WSClient**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-118">In Solution Explorer, right-click **WSClient**, and then click **Build**.</span></span> <span data-ttu-id="51ce8-119">請在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="51ce8-119">Ensure that a success message appears in the output window.</span></span> <span data-ttu-id="51ce8-120">如果沒有成功訊息隨即出現，請疑難排解**WSClient**。</span><span class="sxs-lookup"><span data-stu-id="51ce8-120">If no success message appears, troubleshoot **WSClient**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="51ce8-121">將一份可執行檔，WSClient.exe，放入\<*磁碟機*>: \Tutorial\WSClient\bin\Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="51ce8-121"> places a copy of the executable, WSClient.exe, into the \<*drive*>:\Tutorial\WSClient\bin\Debug folder.</span></span>  
  
 <span data-ttu-id="51ce8-122">若要繼續[步驟 18： 測試您的新訊息擴充方案](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="51ce8-122">Proceed to [Step 18: Test Your New Message Enrichment Solution](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ce8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51ce8-123">See Also</span></span>  
 [<span data-ttu-id="51ce8-124">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="51ce8-124">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)