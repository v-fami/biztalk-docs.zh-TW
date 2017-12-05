---
title: "BizTalk 訊息內文元素未指定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af5d63c0-af96-4e34-828f-d29638cdf46d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0656cf14e1c2a16d6d53966e316550020c8cd0af
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="biztalk-message-body-element-not-specified"></a>未指定 BizTalk 訊息內文元素
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|未指定 BizTalk 訊息內文元素|  
  
## <a name="explanation"></a>說明  
 此錯誤表示使用了輸出 WCF 訊息的範本選項。 但範本運算式不包含 BizTalk 訊息內文元素。  
  
## <a name="user-action"></a>使用者動作  
 請確認範本運算式包含下列項目： \< **bts 訊息主體 xmlns ="http://www.microsoft.com/schemas/bts2007"encoding ="[xml &#124; base64 &#124; 十六進位 &#124; 字串]"/**\>.