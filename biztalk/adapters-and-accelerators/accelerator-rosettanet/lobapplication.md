---
title: LOBApplication |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trading partners, submitting actions
- LOBs, submitting actions
- LOBApplication utility
- trading partners, response messages
- LOBs, LOBApplication utility
- LOBs, response messages
ms.assetid: ad5986af-4175-49cd-806b-04e1fde63f55
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bacce1a64f59d61b5175b10fc14cde1ca862635
ms.sourcegitcommit: 436ebffd959a9c4bdaafd4da9a5843c59a018eb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "34855529"
---
# <a name="lobapplication"></a><span data-ttu-id="bdae7-102">LOBApplication</span><span class="sxs-lookup"><span data-stu-id="bdae7-102">LOBApplication</span></span>
<span data-ttu-id="bdae7-103">您可使用 LOBApplication 公用程式將動作或回應訊息提交給交易夥伴，模擬實際的商務營運系統 (LOB) 桌面程式。</span><span class="sxs-lookup"><span data-stu-id="bdae7-103">You use the LOBApplication utility to submit an action or response message to a trading partner, simulating an actual line-of-business (LOB) desktop program.</span></span>  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="bdae7-104">®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會提供範例訊息中的\<*磁碟機*\>\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bdae7-104">® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides sample messages in the \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="bdae7-105">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="bdae7-105">Location in SDK</span></span>  
 <span data-ttu-id="bdae7-106">\<*磁碟機*\>\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication</span><span class="sxs-lookup"><span data-stu-id="bdae7-106">\<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication</span></span>  
  
## <a name="running-lobapplication"></a><span data-ttu-id="bdae7-107">執行 LOBApplication</span><span class="sxs-lookup"><span data-stu-id="bdae7-107">Running LOBApplication</span></span>  
  
#### <a name="to-run-lobapplication"></a><span data-ttu-id="bdae7-108">若要執行 LOBApplication</span><span class="sxs-lookup"><span data-stu-id="bdae7-108">To run LOBApplication</span></span>  
  
1.  <span data-ttu-id="bdae7-109">在 Windows 檔案總管 中，移至\<*磁碟機*\>\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\\。</span><span class="sxs-lookup"><span data-stu-id="bdae7-109">In Windows Explorer, move to \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\\.</span></span>  
  
2.  <span data-ttu-id="bdae7-110">按兩下**LOBApplication.exe**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="bdae7-110">Double-click **LOBApplication.exe**, and then press ENTER.</span></span>  
  
     <span data-ttu-id="bdae7-111">接下來的頁面會提示您輸入執行公用程式所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="bdae7-111">The pages that follow prompt you for the information that is required to run the utility.</span></span>  
  
## <a name="syntax-for-lobapplication"></a><span data-ttu-id="bdae7-112">LOBApplication 的語法</span><span class="sxs-lookup"><span data-stu-id="bdae7-112">Syntax for LOBApplication</span></span>  
 <span data-ttu-id="bdae7-113">使用**LOB Application Proxy**  頁面來指定主要及交易夥伴的名稱、 交易夥伴介面程序 (PIP) 屬性，以及 LOBApplication 公用程式所傳送之訊息的訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="bdae7-113">Use the **LOB Application Proxy** page to specify home and partner names, Partner Interface Process (PIP) properties, and message properties for the message sent by the LOBApplication utility.</span></span>  
  
 <span data-ttu-id="bdae7-114">下表描述如何使用每個欄位上**LOB Application Proxy**頁面。</span><span class="sxs-lookup"><span data-stu-id="bdae7-114">The following table describes how to use each field on the **LOB Application Proxy** page.</span></span>  
  
|<span data-ttu-id="bdae7-115">使用</span><span class="sxs-lookup"><span data-stu-id="bdae7-115">Use this</span></span>|<span data-ttu-id="bdae7-116">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="bdae7-116">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="bdae7-117">**主要設定檔名稱**</span><span class="sxs-lookup"><span data-stu-id="bdae7-117">**Home Profile Name**</span></span>|<span data-ttu-id="bdae7-118">輸入主要組織 (來源合作對象) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="bdae7-118">Type the name of the home organization (source party).</span></span>|  
|<span data-ttu-id="bdae7-119">**交易夥伴名稱**</span><span class="sxs-lookup"><span data-stu-id="bdae7-119">**Trading Partner Name**</span></span>|<span data-ttu-id="bdae7-120">輸入交易夥伴 (目的合作對象) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="bdae7-120">Type the name of the trading partner (destination party).</span></span>|  
|<span data-ttu-id="bdae7-121">**PIP 名稱**</span><span class="sxs-lookup"><span data-stu-id="bdae7-121">**PIP Name**</span></span>|<span data-ttu-id="bdae7-122">輸入 PIP，例如，類型的顯示代碼**3A2**。</span><span class="sxs-lookup"><span data-stu-id="bdae7-122">Type the display code of the PIP, for example, type **3A2**.</span></span> <span data-ttu-id="bdae7-123">此值區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="bdae7-123">This value is case-sensitive.</span></span>|  
|<span data-ttu-id="bdae7-124">**PIP 版本**</span><span class="sxs-lookup"><span data-stu-id="bdae7-124">**PIP Version**</span></span>|<span data-ttu-id="bdae7-125">輸入 PIP 的版本，例如，類型**V02.00**。</span><span class="sxs-lookup"><span data-stu-id="bdae7-125">Type the version of the PIP, for example, type **V02.00**.</span></span> <span data-ttu-id="bdae7-126">此值區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="bdae7-126">This value is case-sensitive.</span></span>|  
|<span data-ttu-id="bdae7-127">**PIP 執行個體識別碼**（選擇性）</span><span class="sxs-lookup"><span data-stu-id="bdae7-127">**PIP Instance ID** (optional)</span></span>|<span data-ttu-id="bdae7-128">輸入的英數字元的執行個體識別碼的 PIP，例如，輸入**STD_3A2_V02.02**。</span><span class="sxs-lookup"><span data-stu-id="bdae7-128">Type an alphanumeric instance ID for the PIP, for example, type **STD_3A2_V02.02**.</span></span> <span data-ttu-id="bdae7-129">請避免使用特殊字元。</span><span class="sxs-lookup"><span data-stu-id="bdae7-129">Avoid special characters.</span></span> <span data-ttu-id="bdae7-130">每個夥伴和 PIP 代碼的識別碼都應該是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bdae7-130">The ID should be unique per partner and per PIP code.</span></span> <span data-ttu-id="bdae7-131">對於標示為動作訊息的訊息，如果執行個體識別碼是空的，LOBApplication 公用程式就會使用產生的 HUID 值做為 PIP 執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="bdae7-131">For messages that are marked as action messages, if the Instance ID is empty, the LOBApplication utility uses a generated HUID value for the PIP Instance ID.</span></span> <span data-ttu-id="bdae7-132">**注意：** 當您選取**回應**中**訊息類別**，您必須在此欄位中輸入 PIP 執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="bdae7-132">**Note:**  When you select **Response** in the **Message Category**, you must type the PIP Instance ID in this field.</span></span>|  
|<span data-ttu-id="bdae7-133">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="bdae7-133">**File Name**</span></span>|<span data-ttu-id="bdae7-134">按一下省略按鈕 (...)，移至包含 PIP 執行個體檔案的資料夾，然後按一下該 PIP 執行個體檔案。</span><span class="sxs-lookup"><span data-stu-id="bdae7-134">Click the ellipsis button (...), go to the folder that contains the PIP instance file, and then click the PIP instance file.</span></span>|  
|<span data-ttu-id="bdae7-135">**訊息類別**</span><span class="sxs-lookup"><span data-stu-id="bdae7-135">**Message Category**</span></span>|<span data-ttu-id="bdae7-136">選取訊息類型 (**動作**或**回應**)。</span><span class="sxs-lookup"><span data-stu-id="bdae7-136">Select the type of message (**Action** or **Response**).</span></span>|  
|<span data-ttu-id="bdae7-137">**附加檔案**</span><span class="sxs-lookup"><span data-stu-id="bdae7-137">**Attachments**</span></span>|<span data-ttu-id="bdae7-138">按一下**新增**，移至包含附件檔案的資料夾，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="bdae7-138">Click **Add**, move to the folder that contains the attachment file, and then click **Open**.</span></span>|  
|<span data-ttu-id="bdae7-139">**提交訊息**</span><span class="sxs-lookup"><span data-stu-id="bdae7-139">**Submit Message**</span></span>|<span data-ttu-id="bdae7-140">按一下以傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="bdae7-140">Click to send the message.</span></span>|  
|<span data-ttu-id="bdae7-141">**狀態**</span><span class="sxs-lookup"><span data-stu-id="bdae7-141">**Status**</span></span>|<span data-ttu-id="bdae7-142">讀取此欄位中動作的狀態。</span><span class="sxs-lookup"><span data-stu-id="bdae7-142">Read the status of the action in this field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdae7-143">備註</span><span class="sxs-lookup"><span data-stu-id="bdae7-143">Remarks</span></span>  
 <span data-ttu-id="bdae7-144">LOBApplication 公用程式會使用指定的屬性建立訊息，並將它傳送給交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="bdae7-144">The LOBApplication utility creates a message with the properties specified, and sends it to the trading partner.</span></span> <span data-ttu-id="bdae7-145">此公用程式會將訊息中的服務內容資料，寫入至 BTARNDATA 資料庫的 MessageFromLOB 資料表中，</span><span class="sxs-lookup"><span data-stu-id="bdae7-145">This utility writes the service content data in the message to the BTARNDATA database, in the MessageFromLOB table.</span></span> <span data-ttu-id="bdae7-146">並模擬傳送動作訊息。</span><span class="sxs-lookup"><span data-stu-id="bdae7-146">This utility simulates sending an action message.</span></span>  
  
 <span data-ttu-id="bdae7-147">SampleInstances 資料夾 (位於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 的 LOBApplication 資料夾底下) 中的範例訊息會事先設定，以採用下列全球商務識別碼 (GBI)：123456789 代表主要組織，987654321 代表交易夥伴組織。</span><span class="sxs-lookup"><span data-stu-id="bdae7-147">The sample messages in the SampleInstances folder under the LOBApplication folder in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK are preconfigured to assume the following Global Business Identifiers (GBIs): 123456789 for the home organization and 987654321 for the partner organization.</span></span> <span data-ttu-id="bdae7-148">您必須在文字編輯器中變更範例訊息，才可使用其他 GBI。</span><span class="sxs-lookup"><span data-stu-id="bdae7-148">You must change the sample messages in a text editor to use other GBIs.</span></span>  
  
 <span data-ttu-id="bdae7-149">您可使用 LOBApplication 公用程式以模擬商務營運系統桌面程式提交訊息。</span><span class="sxs-lookup"><span data-stu-id="bdae7-149">You use the LOBApplication utility to simulate a line-of-business desktop program submitting a message.</span></span> <span data-ttu-id="bdae7-150">您可以使用 LOBWebApplication 公用程式，模擬商務營運系統 Web 應用程式提交訊息。</span><span class="sxs-lookup"><span data-stu-id="bdae7-150">You use the LOBWebApplication utility to simulate a line-of-business Web application submitting a message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdae7-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdae7-151">See Also</span></span>  
 <span data-ttu-id="bdae7-152">[公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span><span class="sxs-lookup"><span data-stu-id="bdae7-152">[Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span></span>  
 [<span data-ttu-id="bdae7-153">LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="bdae7-153">LOBWebApplication</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)
