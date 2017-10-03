---
title: "BatchTerminator 公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 771241fa-7df5-4882-8430-c2f36200cc9d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64bfb6e708122623040e013d512580beaa37c050
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batchterminator-utility"></a><span data-ttu-id="f3d9b-102">BatchTerminator 公用程式</span><span class="sxs-lookup"><span data-stu-id="f3d9b-102">BatchTerminator Utility</span></span>
<span data-ttu-id="f3d9b-103">BatchTerminator 公用程式可讓您終止所有用來批次處理 EDI 交換的即時批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-103">The BatchTerminator utility enables you to terminate all live batching orchestrations being used to batch EDI interchanges.</span></span> <span data-ttu-id="f3d9b-104">當您擁有大量正在執行的批次處理協調流程執行個體，而您需要終止所有的批次才可以針對 BizTalk 伺服器系統執行維護作業時，這個公用程式保證可發揮其功用。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-104">This utility could prove useful if you have a large number of batching orchestration instances running, and you need to terminate all the batches in order to perform maintenance on the BizTalk server system.</span></span>  
  
 <span data-ttu-id="f3d9b-105">BatchTerminator 公用程式位於[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-105">The BatchTerminator utility is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator folder.</span></span> <span data-ttu-id="f3d9b-106">當您執行公用程式來終止批次處理協調流程執行個體時，此公用程式會將結果記錄在 batchterminator.log 檔案\<*磁碟機*>: \Documents and 設定\\<*使用者名*> \Application Data 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-106">When you run the utility to terminate the batching orchestration instances, the utility will log the results in the batchterminator.log file in the \<*drive*>:\Documents and Settings\\<*user name*>\Application Data folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3d9b-107">BatchTerminator 公用程式才支援在 32 位元系統上。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-107">The BatchTerminator utility is only supported on 32 bit systems.</span></span>  <span data-ttu-id="f3d9b-108">BatchTerminator Microsoft.BizTalk.ExplorerOM 命名空間，才能支援從 32 位元處理序中使用元件。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-108">BatchTerminator uses components in the Microsoft.BizTalk.ExplorerOM namespace, which is only supported if used from a 32 bit process.</span></span>  
  
 <span data-ttu-id="f3d9b-109">**重新啟動終止的協調流程執行個體**</span><span class="sxs-lookup"><span data-stu-id="f3d9b-109">**Restarting the Terminated Orchestration Instances**</span></span>  
  
 <span data-ttu-id="f3d9b-110">當您終止一群協調流程執行個體之後，您就可以針對這些執行個體進行大量重新啟動。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-110">After you terminate a group of batching orchestrations, you can do a bulk restart of those orchestration instances.</span></span> <span data-ttu-id="f3d9b-111">您可以使用 /Activate 參數，以及可指示已遭停止批次之檔案的名稱和路徑，進行這項重新啟動。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-111">You do so with the /Activate switch and the name and path of a file that indicates the batches that were stopped.</span></span> <span data-ttu-id="f3d9b-112">當您執行此公用程式來終止一群協調流程執行個體時，公用程式會建立這個已遭停止批次的檔案。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-112">When you run the utility to terminate a group of orchestration instances, the utility will create this stopped-batches file.</span></span> <span data-ttu-id="f3d9b-113">停止批次檔是 batchSettings-\<GUID > 中的.xml \<*磁碟機*>: \Documents and 設定\\<*使用者名*> \應用程式儲存資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-113">The stopped-batches file is batchSettings-\<GUID>.xml in the \<*drive*>:\Documents and Settings\\<*user name*>\Application Data folder.</span></span> <span data-ttu-id="f3d9b-114">已遭停止批次之檔案的路徑和名稱，也會儲存在該 log 檔案內。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-114">The path and name of the stopped-batches file is also saved in the log file.</span></span> <span data-ttu-id="f3d9b-115">當此公用程式配合 /activate 參數執行時，它會就某個結構描述來驗證輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-115">When the utility runs with the /activate switch, it validates the input file against a schema.</span></span>  
  
 <span data-ttu-id="f3d9b-116">**語法**</span><span class="sxs-lookup"><span data-stu-id="f3d9b-116">**Syntax**</span></span>  
  
 <span data-ttu-id="f3d9b-117">在命令列視窗中，以下列語法來執行 BatchTerminator 公用程式：</span><span class="sxs-lookup"><span data-stu-id="f3d9b-117">Run the BatchTerminator utility in a command-line window with the following syntax:</span></span>  
  
```  
BatchTerminator /<switch>  
```  
  
 <span data-ttu-id="f3d9b-118">您可以配合下列參數來執行 BatchTerminator 公用程式。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-118">You can run the BatchTerminator utility with the following switches.</span></span> <span data-ttu-id="f3d9b-119">若未提供任何參數，則將使用 /terminate 選項。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-119">If no switch is provided, the /terminate option is used.</span></span> <span data-ttu-id="f3d9b-120">正如以下所示，您可以輸入像是 /terminate 的完整參數名稱，或是縮短形式，以此例來說就是 /t。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-120">As indicate below, you can enter the full name of the switch, such as /terminate, or the shortened form, in this case, /t.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3d9b-121">參數</span><span class="sxs-lookup"><span data-stu-id="f3d9b-121">Switch</span></span>|<span data-ttu-id="f3d9b-122">函數</span><span class="sxs-lookup"><span data-stu-id="f3d9b-122">Function</span></span>|  
|<span data-ttu-id="f3d9b-123">/?</span><span class="sxs-lookup"><span data-stu-id="f3d9b-123">/?</span></span>|<span data-ttu-id="f3d9b-124">顯示說明</span><span class="sxs-lookup"><span data-stu-id="f3d9b-124">Displays help</span></span>|  
|<span data-ttu-id="f3d9b-125">/ 結束的記錄檔：\<*記錄檔*></span><span class="sxs-lookup"><span data-stu-id="f3d9b-125">/terminate -log:\<*log file*></span></span><br /><br /> <span data-ttu-id="f3d9b-126">或 /t-記錄檔：\<*記錄檔*></span><span class="sxs-lookup"><span data-stu-id="f3d9b-126">or /t -log:\<*log file*></span></span>|<span data-ttu-id="f3d9b-127">將終止控制訊息傳送給所有作用中的 X12 或 EDIFACT 批次處理協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-127">Sends terminate control messages to all active X12 or EDIFACT batching orchestration instances.</span></span> <span data-ttu-id="f3d9b-128">這個動作會顯示作業的結果，包括它所終止之所有作用中批次協調流程執行個體的清單，它所找到的作用中批次協調流程數目，以及它已傳送的終止控制訊息的數目。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-128">It displays the results of the operation, including a list of all active batch orchestration instances that it terminated, the number of active batch orchestrations that it found, and the number of terminate control messages that it sent.</span></span> <span data-ttu-id="f3d9b-129">它將結果記錄到 batchterminator.log 檔案\<*磁碟機*>: \Documents and 設定\\<*使用者名*> \Application Data 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-129">It logs the results into the batchterminator.log file in the \<*drive*>:\Documents and Settings\\<*user name*>\Application Data folder.</span></span><br /><br /> <span data-ttu-id="f3d9b-130">選用的-記錄： 參數可讓您指定記錄檔的名稱和/或您想要儲存到記錄檔資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-130">The optional -log: parameter enables you to specify the name of the log file and/or the path of the folder that you want the log file to be saved to.</span></span> <span data-ttu-id="f3d9b-131">使用指定的路徑和檔案名稱參數的範例如下所示： `BatchTerminator.exe /terminate -log:"C:\logs\log.txt"`。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-131">An example of using the parameter to specify the path and file name is the following: `BatchTerminator.exe /terminate -log:"C:\logs\log.txt"`.</span></span> <span data-ttu-id="f3d9b-132">使用參數來指定檔案名稱的範例只會如下所示： `BatchTerminator.exe /terminate -log:log.txt`。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-132">An example of using the parameter to specify the file name only is the following: `BatchTerminator.exe /terminate -log:log.txt`.</span></span> <span data-ttu-id="f3d9b-133">如果指定的路徑無效，此公用程式會使用預設路徑： \<*磁碟機*>: \Documents and 設定\\<*使用者名*> \Application 資料。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-133">If the path specified is invalid, the utility will use the default path: \<*drive*>:\Documents and Settings\\<*user name*>\Application Data.</span></span> <span data-ttu-id="f3d9b-134">-Log： 參數可以用，不論 /terminate 參數。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-134">The -log: parameter can be used either with or without the /terminate switch.</span></span>|  
|<span data-ttu-id="f3d9b-135">/print</span><span class="sxs-lookup"><span data-stu-id="f3d9b-135">/print</span></span><br /><br /> <span data-ttu-id="f3d9b-136">或 /p</span><span class="sxs-lookup"><span data-stu-id="f3d9b-136">or /p</span></span>|<span data-ttu-id="f3d9b-137">顯示一份不傳送終止控制訊息之目前作用中批次處理協調流程執行個體的清單</span><span class="sxs-lookup"><span data-stu-id="f3d9b-137">Displays a listing of the current active batching orchestration instances without sending terminate control messages</span></span>|  
|<span data-ttu-id="f3d9b-138">啟動 /:\<*路徑*>\\</span><span class="sxs-lookup"><span data-stu-id="f3d9b-138">/activate:\<*path*>\\</span></span><br /><span data-ttu-id="f3d9b-139">batchSettings-\<*GUID*>.xml-記錄檔：\<*記錄檔*></span><span class="sxs-lookup"><span data-stu-id="f3d9b-139">batchSettings-\<*GUID*>.xml -log:\<*log file*></span></span><br /><br /> <span data-ttu-id="f3d9b-140">或 /a:\<*路徑*>\\</span><span class="sxs-lookup"><span data-stu-id="f3d9b-140">or /a:\<*path*>\\</span></span><br /><span data-ttu-id="f3d9b-141">batchSettings-\<*GUID*>.xml-記錄檔：\<*記錄檔*></span><span class="sxs-lookup"><span data-stu-id="f3d9b-141">batchSettings-\<*GUID*>.xml -log:\<*log file*></span></span>|<span data-ttu-id="f3d9b-142">重新啟動先前已終止的協調流程執行個體所述的 batchSettings-\<GUID >.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-142">Reactivates the previously terminated orchestration instances that are listed in the batchSettings-\<GUID>.xml file.</span></span> <span data-ttu-id="f3d9b-143">公用程式會就程式碼內嵌的結構描述，驗證該輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-143">The utility will validate the input file against a schema embedded in the code.</span></span> <span data-ttu-id="f3d9b-144">如果該輸入檔案與該結構描述不相符，這時螢幕上就會印出錯誤訊息，而該程式將會結束。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-144">If the input file does not match the schema, an error message will be printed to the screen and the program will exit.</span></span><br /><br /> <span data-ttu-id="f3d9b-145">若有包括 -log: 參數，這個作業就會將關於重新啟動動作的資訊寫入至記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-145">This operation writes information about the restarting action in the log file if you include the -log: switch.</span></span>|  
  
 <span data-ttu-id="f3d9b-146">**批次啟動檔案的格式**</span><span class="sxs-lookup"><span data-stu-id="f3d9b-146">**Format of the Batch Activation File**</span></span>  
  
 <span data-ttu-id="f3d9b-147">若要重新啟用之前終止批次協調流程執行個體使用 / 啟動參數，您必須提供批次啟動檔案 (batchSettings-\<GUID >.xml)。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-147">To reactivate previously terminated batch orchestration instances by using the /activate switch, you must provide a batch activation file (batchSettings-\<GUID>.xml).</span></span> <span data-ttu-id="f3d9b-148">這個檔案必須採用下列格式：</span><span class="sxs-lookup"><span data-stu-id="f3d9b-148">This file must be in the following format:</span></span>  
  
```  
<?xml version="1.0"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" elementFormDefault="qualified" id="BatchInfo" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="BatchTerminator">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="Batch">  
          <xs:complexType>  
            <xs:attribute name="PartyName" type="xs:string" />  
            <xs:attribute name="PartyID" type="xs:int" use="required" />  
            <xs:attribute name=”BatchName” type=”xs:string” />  
            <xs:attribute name=”BatchID” type=”xs:int” use=”required” />  
            <xs:attribute name="EdiMessageType" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="prerequisites"></a><span data-ttu-id="f3d9b-149">必要條件</span><span class="sxs-lookup"><span data-stu-id="f3d9b-149">Prerequisites</span></span>  
 <span data-ttu-id="f3d9b-150">下列是執行本主題所述程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="f3d9b-150">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="f3d9b-151">您必須以「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-151">You must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-run-the-batchterminator-utility"></a><span data-ttu-id="f3d9b-152">若要執行 BatchTerminator 公用程式</span><span class="sxs-lookup"><span data-stu-id="f3d9b-152">To run the BatchTerminator utility</span></span>  
  
1.  <span data-ttu-id="f3d9b-153">在 Windows 檔案總管 中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-153">In Windows Explorer, move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator folder.</span></span>  
  
2.  <span data-ttu-id="f3d9b-154">Enter **BatchTerminator**，包括任何需要的參數，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-154">Enter **BatchTerminator**, including any desired switches, and then click **Enter**.</span></span>  
  
3.  <span data-ttu-id="f3d9b-155">在 Windows 檔案總管 中，移至\<*磁碟機*>: \Documents and 設定\\<*使用者名*> \Application 資料資料夾，然後開啟 batchterminator.log若要查看結果的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f3d9b-155">In Windows Explorer, move to \<*drive*>:\Documents and Settings\\<*user name*>\Application Data folder, and open the batchterminator.log file to see a log of the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d9b-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3d9b-156">See Also</span></span>  
 [<span data-ttu-id="f3d9b-157">在 SDK 中的公用程式</span><span class="sxs-lookup"><span data-stu-id="f3d9b-157">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)