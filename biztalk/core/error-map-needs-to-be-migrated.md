---
title: 錯誤-對應需要移轉 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.mapNeedsMigrating
ms.assetid: f10af4a4-6e40-4eec-a2fd-e526821aebe6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f49ef4aae0db47216f6117f1053185df6fae0a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---map-needs-to-be-migrated"></a><span data-ttu-id="0391a-102">錯誤-對應需要移轉</span><span class="sxs-lookup"><span data-stu-id="0391a-102">Error - Map Needs to be Migrated</span></span>
<span data-ttu-id="0391a-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="0391a-103">**Error Code**</span></span>  
  
 <span data-ttu-id="0391a-104">btm1064</span><span class="sxs-lookup"><span data-stu-id="0391a-104">btm1064</span></span>  
  
 <span data-ttu-id="0391a-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="0391a-105">**Explanation**</span></span>  
  
 <span data-ttu-id="0391a-106">無法編譯對應，因為它是使用舊版 BizTalk 對應工具所建立。</span><span class="sxs-lookup"><span data-stu-id="0391a-106">The map cannot be compiled because it was created using a previous version of BizTalk Mapper.</span></span> <span data-ttu-id="0391a-107">您必須將此類對應移轉至此版本 BizTalk 對應工具，才能編譯該對應。</span><span class="sxs-lookup"><span data-stu-id="0391a-107">You must migrate such maps to this version of BizTalk Mapper before they can be compiled.</span></span>  
  
 <span data-ttu-id="0391a-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="0391a-108">**User Action**</span></span>  
  
 <span data-ttu-id="0391a-109">將對應移轉至目前的 BizTalk 對應工具版本，方式是將其副檔名從 "xml" 更改為 "btm"，並將它新增到相關 Microsoft BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="0391a-109">Migrate the map to the current version of BizTalk Mapper by changing its file extension from "xml" to "btm", adding it to the relevant Microsoft BizTalk Server project.</span></span> <span data-ttu-id="0391a-110">使用**加入現有項目**命令，或使用**檔案**功能表和捷徑功能表，biztalk 專案在方案總管 中，按兩下方案總管 中，以開啟對應。</span><span class="sxs-lookup"><span data-stu-id="0391a-110">Use the **Add Existing Item** command available on the **File** menu and on the shortcut menu for the BizTalk project in Solution Explorer, and then open the map by double-clicking it in Solution Explorer.</span></span> <span data-ttu-id="0391a-111">因為您已在檢視本主題，您可以能已執行前兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="0391a-111">Because you have reached this topic, you have probably already performed the first two steps.</span></span> <span data-ttu-id="0391a-112">只要在目前版本的 BizTalk 對應工具中開啟開對應，即可執行即時移轉對應作業。</span><span class="sxs-lookup"><span data-stu-id="0391a-112">Simply opening the map in the current version of BizTalk Mapper will perform an on-the-fly migration of the map.</span></span>