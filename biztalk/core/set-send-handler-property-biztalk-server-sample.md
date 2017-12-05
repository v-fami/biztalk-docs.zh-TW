---
title: "設定 Send Handler 屬性 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- send handlers, properties
ms.assetid: eb6ae2f2-528f-44ec-bca4-f37006893ff2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f783f465feff207ae1759ea358b0b848ccc0f4c3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="set-send-handler-property-biztalk-server-sample"></a><span data-ttu-id="fe1cf-102">設定 Send Handler 屬性 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="fe1cf-102">Set Send Handler Property (BizTalk Server Sample)</span></span>
<span data-ttu-id="fe1cf-103">設定 Send Handler 屬性範例會示範如何設定 Simple Mail Transfer Protocol (SMTP) 傳送處理常式的 XML 組態資訊。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-103">The Set Send Handler Property sample demonstrates how to set the XML configuration information for a Simple Mail Transfer Protocol (SMTP) send handler.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fe1cf-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="fe1cf-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="fe1cf-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="fe1cf-106">What This Sample Does</span></span>  
 <span data-ttu-id="fe1cf-107">構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="fe1cf-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="fe1cf-108">在指定傳送處理常式名稱情況下，查詢相符傳送處理常式的清單。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-108">Given a send handler name, query for a list of matching send handlers.</span></span>  
  
-   <span data-ttu-id="fe1cf-109">設定 SMTP 傳送處理常式的 XML 組態資訊。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-109">Set the XML configuration information for an SMTP send handler.</span></span>  
  
-   <span data-ttu-id="fe1cf-110">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-110">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="fe1cf-111">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="fe1cf-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="fe1cf-112">這些範例檔案位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="fe1cf-112">The sample files are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="fe1cf-113">\<*範例路徑*\>\Admin\WMI\Set 傳送處理常式 Property\\</span><span class="sxs-lookup"><span data-stu-id="fe1cf-113">\<*Samples Path*\>\Admin\WMI\Set Send Handler Property\\</span></span>  
  
 <span data-ttu-id="fe1cf-114">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-114">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="fe1cf-115">檔案</span><span class="sxs-lookup"><span data-stu-id="fe1cf-115">File(s)</span></span>|<span data-ttu-id="fe1cf-116">Description</span><span class="sxs-lookup"><span data-stu-id="fe1cf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe1cf-117">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="fe1cf-117">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="fe1cf-118">ConfigureSMTP.vbs</span><span class="sxs-lookup"><span data-stu-id="fe1cf-118">ConfigureSMTP.vbs</span></span>|<span data-ttu-id="fe1cf-119">VBScript 檔案，它會接受多個參數，而這些參數會指定 SMTP 傳送處理常式和「寄件者」電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-119">VBScript file that takes parameters that specify an SMTP send handler and a From e-mail address.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="fe1cf-120">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="fe1cf-120">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="fe1cf-121">「設定 Send Handler 屬性」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-121">The Set Send Handler Property sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="fe1cf-122">執行此範例</span><span class="sxs-lookup"><span data-stu-id="fe1cf-122">Running This Sample</span></span>  
  
#### <a name="to-run-the-set-send-handler-property-sample"></a><span data-ttu-id="fe1cf-123">若要執行設定 Send Handler 屬性範例</span><span class="sxs-lookup"><span data-stu-id="fe1cf-123">To run the Set Send Handler Property sample</span></span>  
  
1.  <span data-ttu-id="fe1cf-124">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="fe1cf-124">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="fe1cf-125">\<*範例路徑*\>\Admin\WMI\Set 傳送處理常式 Property\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="fe1cf-125">\<*Samples Path*\>\Admin\WMI\Set Send Handler Property\VBScript\\</span></span>  
  
2.  <span data-ttu-id="fe1cf-126">執行 ConfigureSMTP.vbs 檔案，它會使用 cscript 程式，並傳遞下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="fe1cf-126">Run the file ConfigureSMTP.vbs using the cscript program, passing the following command-line argument:</span></span>  
  
    -   <span data-ttu-id="fe1cf-127">**\<** ***SMTPServerName* \>。**</span><span class="sxs-lookup"><span data-stu-id="fe1cf-127">**\<** ***SMTPServerName* \>.**</span></span> <span data-ttu-id="fe1cf-128">將會用來傳送郵件之 SMTP 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-128">The name of the SMTP server that will be used to send mail.</span></span>  
  
    -   <span data-ttu-id="fe1cf-129">**\<** ***FromEmailAddress* \>。**</span><span class="sxs-lookup"><span data-stu-id="fe1cf-129">**\<** ***FromEmailAddress* \>.**</span></span> <span data-ttu-id="fe1cf-130">將會用來做為「寄件者」地址的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-130">An e-mail address that will be used as the From address.</span></span>  
  
         <span data-ttu-id="fe1cf-131">例如：</span><span class="sxs-lookup"><span data-stu-id="fe1cf-131">For example:</span></span>  
  
        ```  
        cscript ConfigureSMTP.vbs MyBusinessSMTPServer someone@example.com  
        ```  
  
## <a name="comments"></a><span data-ttu-id="fe1cf-132">註解</span><span class="sxs-lookup"><span data-stu-id="fe1cf-132">Comments</span></span>  
 <span data-ttu-id="fe1cf-133">您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-133">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="fe1cf-134">指令檔 ConfigureSMTP.vbs 包含詳細註解，其中含有其所執行作業的深入說明。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-134">The script file ConfigureSMTP.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="fe1cf-135">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="fe1cf-135">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1cf-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe1cf-136">See Also</span></span>  
 [<span data-ttu-id="fe1cf-137">Admin-WMI (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="fe1cf-137">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)