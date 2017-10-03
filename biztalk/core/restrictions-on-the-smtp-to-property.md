---
title: "限制屬性 SMTP |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- SMTP adapters, restrictions
ms.assetid: c876d30e-44ab-462d-8c98-64416ed6dd1f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b59495ac94b3591801101607533eb9c7dba158fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-the-smtp-to-property"></a>屬性至 SMTP 的限制
**至**屬性會指定訊息的收件者的 SMTP 位址的字串。 您可以列出多個 SMTP 伺服器支援的位址，以分隔符號區隔。  
  
 SMTP 位址的格式沒有特定限制。 這表示配接器會接受 SMTP 伺服器支援的任何格式。 若使用者提供無效的位址，傳送作業就會失敗，而 SMTP 傳送配接器會報告錯誤。  
  
 對此屬性的唯一限制就是它不能是空白，且大小不得超過 256 個字元。  
  
## <a name="see-also"></a>另請參閱  
 [設定 SMTP 配接器時的限制](../core/restrictions-when-configuring-the-smtp-adapter.md)