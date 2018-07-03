---
title: BtarnConfig |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTARN, exporting configuration data
- BTARN, BtarnConfig utility
- BtarnConfig utility
- BTARN, importing configuration data
ms.assetid: 8c95be2a-7df5-47fb-ae2d-64fa27e2811a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 542ed5729ce4f5ed7ca4a6d453b3169bb1f43d01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991463"
---
# <a name="btarnconfig"></a><span data-ttu-id="110b0-102">BtarnConfig</span><span class="sxs-lookup"><span data-stu-id="110b0-102">BtarnConfig</span></span>
<span data-ttu-id="110b0-103">您使用 BtarnConfig 公用程式匯入組態資料，或匯出組態資料從 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="110b0-103">You use the BtarnConfig utility to import configuration data into, or export configuration data from, a Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] environment.</span></span> <span data-ttu-id="110b0-104">組態資料便是使用 BTARN 管理主控台設定的資料，其中包括有程序組態設定、主要組織、夥伴和協議。</span><span class="sxs-lookup"><span data-stu-id="110b0-104">This configuration data is the data that you set by using the BTARN Management Console, including process configuration settings, home organizations, partners, and agreements.</span></span>  

## <a name="location-in-sdk"></a><span data-ttu-id="110b0-105">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="110b0-105">Location in SDK</span></span>  
 <span data-ttu-id="110b0-106">\<*磁碟機*\>\ Program Files (x86)\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK</span><span class="sxs-lookup"><span data-stu-id="110b0-106">\<*drive*\>\ Program Files (x86)\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK</span></span>  

## <a name="running-btarnconfig"></a><span data-ttu-id="110b0-107">執行 BtarnConfig</span><span class="sxs-lookup"><span data-stu-id="110b0-107">Running BtarnConfig</span></span>  

#### <a name="to-run-btarnconfig"></a><span data-ttu-id="110b0-108">若要執行 BtarnConfig</span><span class="sxs-lookup"><span data-stu-id="110b0-108">To run BtarnConfig</span></span>  

1. <span data-ttu-id="110b0-109">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="110b0-109">Open a command prompt.</span></span>  

2. <span data-ttu-id="110b0-110">移至\<*磁碟機*\>\ Program Files (x86)\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\\。</span><span class="sxs-lookup"><span data-stu-id="110b0-110">Move to \<*drive*\>\ Program Files (x86)\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\\.</span></span>  

3. <span data-ttu-id="110b0-111">在命令提示字元中，輸入**BtarnConfig**，輸入適當的參數，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="110b0-111">At the command prompt, type **BtarnConfig**, type the appropriate switches, and then press ENTER.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="110b0-112">下節會說明這些參數。</span><span class="sxs-lookup"><span data-stu-id="110b0-112">The following section describes the switches.</span></span>  

## <a name="syntax-for-btarnconfig"></a><span data-ttu-id="110b0-113">BtarnConfig 的語法</span><span class="sxs-lookup"><span data-stu-id="110b0-113">Syntax for BtarnConfig</span></span>  
 <span data-ttu-id="110b0-114">以下是用來啟動這個命令列工具的語法：</span><span class="sxs-lookup"><span data-stu-id="110b0-114">The following shows the syntax that you use to start this command-line tool:</span></span>  

### <a name="syntax-for-importing-configuration-data"></a><span data-ttu-id="110b0-115">用來匯入組態資料的語法</span><span class="sxs-lookup"><span data-stu-id="110b0-115">Syntax for Importing Configuration Data</span></span>  

```  
BTARNCONFIG /IMPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  

### <a name="syntax-for-exporting-configuration-data"></a><span data-ttu-id="110b0-116">用來匯出組態資料的語法</span><span class="sxs-lookup"><span data-stu-id="110b0-116">Syntax for Exporting Configuration Data</span></span>  

```  
BTARNCONFIG /EXPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  

### <a name="syntax-description"></a><span data-ttu-id="110b0-117">語法描述</span><span class="sxs-lookup"><span data-stu-id="110b0-117">Syntax Description</span></span>  
 <span data-ttu-id="110b0-118">下表說明 BtarnConfig 公用程式所使用語法的每個部分。</span><span class="sxs-lookup"><span data-stu-id="110b0-118">The following table describes each part of the syntax that the BtarnConfig utility uses.</span></span>  


|       <span data-ttu-id="110b0-119">語法</span><span class="sxs-lookup"><span data-stu-id="110b0-119">Syntax</span></span>       |                                                                                                                          <span data-ttu-id="110b0-120">描述</span><span class="sxs-lookup"><span data-stu-id="110b0-120">Description</span></span>                                                                                                                          |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="110b0-121">\<*檔名*.xml\></span><span class="sxs-lookup"><span data-stu-id="110b0-121">\<*filename*.xml\></span></span> | <span data-ttu-id="110b0-122">匯入或匯出檔案的來源或目的地的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="110b0-122">Full path of the file to import into or export from.</span></span> <span data-ttu-id="110b0-123">如果您未提供路徑，BTARN 會假設路徑是否\<*磁碟機*\>\ Program Files (x86)\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK。</span><span class="sxs-lookup"><span data-stu-id="110b0-123">If you do not provide a path, BTARN assumes that the path is \<*drive*\>\ Program Files (x86)\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK.</span></span> |
|    <span data-ttu-id="110b0-124">**/ 匯入**</span><span class="sxs-lookup"><span data-stu-id="110b0-124">**/IMPORT**</span></span>     |                                                                                          <span data-ttu-id="110b0-125">從 XML 資料匯入\<*檔名*.xml\> BTARN 組態。</span><span class="sxs-lookup"><span data-stu-id="110b0-125">Imports the XML data from \<*filename*.xml\> into the BTARN configuration.</span></span>                                                                                           |
|    <span data-ttu-id="110b0-126">**/EXPORT**</span><span class="sxs-lookup"><span data-stu-id="110b0-126">**/EXPORT**</span></span>     |                                                                                             <span data-ttu-id="110b0-127">將 BTARN 組態匯出為 XML 資料轉換成\<*檔名*.xml\>。</span><span class="sxs-lookup"><span data-stu-id="110b0-127">Exports the BTARN configuration as XML data into \<*filename*.xml\>.</span></span>                                                                                              |
|       <span data-ttu-id="110b0-128">**/H**</span><span class="sxs-lookup"><span data-stu-id="110b0-128">**/H**</span></span>       |                                                                                                   <span data-ttu-id="110b0-129">匯入或匯出主要組織的組態資料。</span><span class="sxs-lookup"><span data-stu-id="110b0-129">Imports or exports home-organization configuration data.</span></span>                                                                                                    |
|       <span data-ttu-id="110b0-130">**/P**</span><span class="sxs-lookup"><span data-stu-id="110b0-130">**/P**</span></span>       |                                                                                                        <span data-ttu-id="110b0-131">匯入或匯出交易夥伴的組態資料。</span><span class="sxs-lookup"><span data-stu-id="110b0-131">Imports or exports partner configuration data.</span></span>                                                                                                         |
|       <span data-ttu-id="110b0-132">**/R**</span><span class="sxs-lookup"><span data-stu-id="110b0-132">**/R**</span></span>       |                                                                                                        <span data-ttu-id="110b0-133">匯入或匯出程序的組態資料。</span><span class="sxs-lookup"><span data-stu-id="110b0-133">Imports or exports process configuration data.</span></span>                                                                                                         |
|       <span data-ttu-id="110b0-134">**/A**</span><span class="sxs-lookup"><span data-stu-id="110b0-134">**/A**</span></span>       |                                                                                                       <span data-ttu-id="110b0-135">匯入或匯出協議的組態資料。</span><span class="sxs-lookup"><span data-stu-id="110b0-135">Imports or exports agreement configuration data.</span></span>                                                                                                        |

## <a name="remarks"></a><span data-ttu-id="110b0-136">備註</span><span class="sxs-lookup"><span data-stu-id="110b0-136">Remarks</span></span>  
 <span data-ttu-id="110b0-137">如果您未提供的任一 **/H**， **/P**， **/R**，或 **/A**參數的 BtarnConfig 公用程式匯入或匯出所有資料。</span><span class="sxs-lookup"><span data-stu-id="110b0-137">If you do not provide any one of the **/H**, **/P**, **/R**, or **/A** switches, the BtarnConfig utility imports or exports all the data.</span></span> <span data-ttu-id="110b0-138">在一次作業中就匯出所有的資料時，BtarnConfig 會依照下列順序，將這些資料匯出為 XML 檔案：主要組織、交易夥伴、程序組態和協議。</span><span class="sxs-lookup"><span data-stu-id="110b0-138">When you export all the data in one operation, BtarnConfig exports the data into the XML file in the following order: home organizations, partners, process configuration, and agreements.</span></span>  

 <span data-ttu-id="110b0-139">如果您正要進行匯入作業的來源檔案中，存在結構性的問題，BTARN 將會在結構描述驗證階段期間，偵測到錯誤。因此在資料尚未匯入之前，作業就會失敗。</span><span class="sxs-lookup"><span data-stu-id="110b0-139">If there is a structural problem with the file that you are importing from, BTARN will detect the error during the schema validation stage, and the operation will fail before any data is imported.</span></span> <span data-ttu-id="110b0-140">如果發生其他錯誤，例如您正在嘗試匯入複製的成品或是 PIP/協議需要 HTTPS，則匯入作業也會失敗。</span><span class="sxs-lookup"><span data-stu-id="110b0-140">If another error occurs, for example, you are trying to import a duplicate artifact or HTTPS is required for the PIP/agreement, then the import operation will fail.</span></span> <span data-ttu-id="110b0-141">然而，所有已匯入該位置的資料將會持續保留在組態中。</span><span class="sxs-lookup"><span data-stu-id="110b0-141">However, all the data imported up to that point will remain in the configuration.</span></span>  

 <span data-ttu-id="110b0-142">您必須是 BizTalk 系統管理員，才能使用 BtarnConfig 進行組態資料的匯入或匯出作業。</span><span class="sxs-lookup"><span data-stu-id="110b0-142">You must be a BizTalk administrator to import or export configuration data using BtarnConfig.</span></span> <span data-ttu-id="110b0-143">如果您不是 BizTalk 系統管理員，某些匯入作業會因為存取權限的問題而失敗。</span><span class="sxs-lookup"><span data-stu-id="110b0-143">If you are not a BizTalk administrator, some import operations may fail because of access issues.</span></span> <span data-ttu-id="110b0-144">但是，其他以相同 BtarnConfig 命令進行的匯入作業則有可能會成功。</span><span class="sxs-lookup"><span data-stu-id="110b0-144">However,  other import operations in the same BtarnConfig command may succeed.</span></span>  

## <a name="see-also"></a><span data-ttu-id="110b0-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="110b0-145">See Also</span></span>  
 [<span data-ttu-id="110b0-146">公用程式</span><span class="sxs-lookup"><span data-stu-id="110b0-146">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
