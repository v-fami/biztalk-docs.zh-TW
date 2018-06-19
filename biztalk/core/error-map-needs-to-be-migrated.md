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
ms.locfileid: "22240550"
---
# <a name="error---map-needs-to-be-migrated"></a>錯誤-對應需要移轉
**錯誤碼**  
  
 btm1064  
  
 **說明**  
  
 無法編譯對應，因為它是使用舊版 BizTalk 對應工具所建立。 您必須將此類對應移轉至此版本 BizTalk 對應工具，才能編譯該對應。  
  
 **使用者動作**  
  
 將對應移轉至目前的 BizTalk 對應工具版本，方式是將其副檔名從 "xml" 更改為 "btm"，並將它新增到相關 Microsoft BizTalk Server 專案。 使用**加入現有項目**命令，或使用**檔案**功能表和捷徑功能表，biztalk 專案在方案總管 中，按兩下方案總管 中，以開啟對應。 因為您已在檢視本主題，您可以能已執行前兩個步驟。 只要在目前版本的 BizTalk 對應工具中開啟開對應，即可執行即時移轉對應作業。