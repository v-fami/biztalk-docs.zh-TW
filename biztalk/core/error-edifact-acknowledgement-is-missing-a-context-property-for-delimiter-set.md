---
title: "EDIFACT 通知由系統產生。 不過，它的分隔符號設定遺失的內容屬性。 無法序列化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d7b1e62-3230-4cdc-830f-3267de1efd1c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d21ce485c2cd5c55bb941afdfc15d2ad545db61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-edifact-acknowledgement-was-generated-by-the-system-however-it-is-missing-a-context-property-for-delimiter-set-it-cannot-be-serialized"></a>EDIFACT 通知由系統產生。 不過，它的分隔符號設定遺失的內容屬性。 無法序列化
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|EDIFACT 通知由系統產生。 不過，它的分隔符號設定遺失的內容屬性。 無法序列化|  
  
## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk Server 無法序列化 EDIFACT 通知和分隔符號設定內容屬性是從 BizTalk 訊息中遺失。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請務必分隔符號設定內容屬性寫入 BizTalk 訊息內容，對於 EDIFACT 通知。