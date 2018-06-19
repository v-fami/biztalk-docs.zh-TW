---
title: 步驟 3： 測試移轉的 Application2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Send IDOC)
- migration
ms.assetid: 8dc0d127-71ce-4668-a3bf-c893a8f6848d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dbf6154337dc9daf5dcfe75b3f5b7299ae843ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216462"
---
# <a name="step-3-test-the-migrated-application"></a><span data-ttu-id="ab09a-102">步驟 3： 測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="ab09a-102">Step 3: Test the Migrated Application</span></span>
<span data-ttu-id="ab09a-103">![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="ab09a-103">![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="ab09a-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="ab09a-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="ab09a-105">**目標：** 在此步驟中，您會測試已移轉的應用程式使用 WCF 為基礎的一般檔案 IDOC 的傳送[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ab09a-105">**Objective:** In this step, you will test the migrated application by sending a flat-file IDOC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ab09a-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="ab09a-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="ab09a-107">將 BizTalk 協調流程中的邏輯連接埠對應至實體連接埠，BizTalk Server 管理主控台中設定的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab09a-107">Configure the BizTalk application by mapping the logical ports in the BizTalk orchestration to physical ports in the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="ab09a-108">設定要用於 wcf-custom 傳送埠以 WCF 為基礎的 BizTalk 應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ab09a-108">Configure the BizTalk application to use the WCF-custom send port for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
### <a name="to-test-the-migrated-application"></a><span data-ttu-id="ab09a-109">若要測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="ab09a-109">To test the migrated application</span></span>  
  
1.  <span data-ttu-id="ab09a-110">從 [SendIDOC_Migration] 資料夾中，複製 BOMDOC.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab09a-110">From the SendIDOC_Migration folder, copy the BOMDOC.txt file.</span></span> <span data-ttu-id="ab09a-111">這是要傳送到 SAP 系統的一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="ab09a-111">This is the flat-file IDOC to be sent to the SAP system.</span></span>  
  
2.  <span data-ttu-id="ab09a-112">貼上的資料夾對應到檔案，一般檔案 IDOC 的接收位置。</span><span class="sxs-lookup"><span data-stu-id="ab09a-112">Paste the flat-file IDOC to the folder that is mapped to the file receive location.</span></span>  
  
3.  <span data-ttu-id="ab09a-113">協調流程使用檔，並傳送 IDOC 至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ab09a-113">The orchestration consumes the file and sends the IDOC to the SAP system.</span></span> <span data-ttu-id="ab09a-114">請檢查事件檢視器中是否有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab09a-114">Verify if there are any errors in the event viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab09a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab09a-115">See Also</span></span>  
 [<span data-ttu-id="ab09a-116">教學課程 3： 移轉 SAP 傳送 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="ab09a-116">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)