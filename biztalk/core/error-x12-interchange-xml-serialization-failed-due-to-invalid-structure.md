---
title: "X12 交換 Xml 序列化失敗，因為無效的結構。 尋找 TransactionSet 或 GE，但找不到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d058fdbb-6be5-499f-86f7-0eb8a85c5fb2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3d4081c901e95dbd1b9911b2cd957dbe7319761
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="x12-interchange-xml-serialization-failed-due-to-invalid-structure-looking-for-transactionset-or-ge-but-not-found"></a>X12 交換 Xml 序列化失敗，因為無效的結構。 尋找 TransactionSet 或 GE，但找不到
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TransactionSetOrGeNotFound|  
|訊息文字|X12 交換 Xml 序列化失敗，因為無效的結構。 尋找 TransactionSet 或 GE，但找不到|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法序列化到外寄交換因為交換的結構無效。 原因可能是必要的標頭或結尾不存在或無效。 如果設定群組中的交易之後沒有接著另一個交易集或群組結尾，它可能會發生。 它可能也會發生結構完整性檢查失敗。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認交換，以確保群組或交易集標頭和結尾有效，然後再重新傳送交換的結構。