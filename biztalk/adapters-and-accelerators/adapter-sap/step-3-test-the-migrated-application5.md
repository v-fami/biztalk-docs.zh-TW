---
title: 步驟 3： 測試已移轉的 Application5 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Receive IDOC)
- migration
ms.assetid: 3ad15069-1556-4c0a-8bfd-86704d40c586
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195b150dcbc3edcd1bfe0a18a17c6fe73cb4f50b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009143"
---
# <a name="step-3-test-the-migrated-application"></a><span data-ttu-id="3fd54-102">步驟 3： 測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="3fd54-102">Step 3: Test the Migrated Application</span></span>
<span data-ttu-id="3fd54-103">![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="3fd54-103">![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="3fd54-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="3fd54-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="3fd54-105">**目標：** 在此步驟中，您將測試已移轉的應用程式以接收使用以 WCF 為基礎的一般檔案 IDOC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3fd54-105">**Objective:** In this step, you will test the migrated application by receiving a flat-file IDOC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3fd54-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="3fd54-106">Prerequisites</span></span>  
  
- <span data-ttu-id="3fd54-107">將 BizTalk 協調流程中的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠，以設定 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3fd54-107">Configure the BizTalk application by mapping the logical ports in the BizTalk orchestration to physical ports in the BizTalk Server Administration console.</span></span>  
  
- <span data-ttu-id="3fd54-108">設定 BizTalk 應用程式使用 WCF 自訂接收埠，讓 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3fd54-108">Configure the BizTalk application to use the WCF-Custom receive port for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
### <a name="to-test-the-migrated-application"></a><span data-ttu-id="3fd54-109">若要測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="3fd54-109">To test the migrated application</span></span>  
  
1.  <span data-ttu-id="3fd54-110">啟動 SAP GUI 中，並連接到您在 連線 URI 中指定的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="3fd54-110">Start the SAP GUI, and connect to the SAP system that you specified in the connection URI.</span></span>  
  
2.  <span data-ttu-id="3fd54-111">執行 SE37，並叫用 SAP 傳送 IDOC 至外部系統中的函式模組。</span><span class="sxs-lookup"><span data-stu-id="3fd54-111">Run SE37, and invoke a function module in SAP that sends an IDOC to an external system.</span></span> <span data-ttu-id="3fd54-112">請確定您傳送 IDOC 使用 Wcf-custom 接收埠，會將連線 URI 中指定的同一個程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="3fd54-112">Make sure you send the IDOC using the same program ID that is specified in the connection URI for the WCF-Custom receive port.</span></span>  
  
3.  <span data-ttu-id="3fd54-113">輸入 IDOC 的協調流程中指定的檔案位置的外觀。</span><span class="sxs-lookup"><span data-stu-id="3fd54-113">Look for the inbound IDOC at the file location specified as part of the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd54-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fd54-114">See Also</span></span>  
 [<span data-ttu-id="3fd54-115">教學課程 4：移轉 SAP 接收 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="3fd54-115">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)