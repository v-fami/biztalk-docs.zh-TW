---
title: 專案位置不是空白 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db353050-3662-4ab6-8898-4e4d3bd78ac1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fc106b534973f13544b9bafa85f190d8ed2c255
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994287"
---
# <a name="the-project-location-is-not-empty"></a>專案位置不是空白的
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                 |
| 產品版本 |                                                                                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                             |
|    事件識別碼     |                                                                                                                         0                                                                                                                          |
|  事件來源   |                                                                                                                         0                                                                                                                          |
|    元件    |                                                                                                                         0                                                                                                                          |
|  符號名稱  |                                                                                                                         0                                                                                                                          |
|  訊息文字   | 專案位置"{0}"不是空的。 您需要執行下列其中之一： 1。 選擇新專案，也就是 2 的不同位置。 指定覆寫重新使用現用位置或 3。 手動刪除專案位置的內容。 |
  
## <a name="explanation"></a>說明  
 此錯誤表示嘗試將服務發佈到的虛擬目錄不是空的。  
  
## <a name="user-action"></a>使用者動作  
 選取覆寫位置重複使用相同的位置。 或指定新的位置。  在 [WCF 服務發佈精靈，選取**覆寫現有的位置**然後按一下**下一步]**。 此步驟會覆寫位置。