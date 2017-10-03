---
title: "擴充 (BTS-XSD) 驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f225115d-8890-4149-8e46-d1bc8af17e62
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed147515b48a23c55e552710d6a76d6df981edd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="extended-bts-xsd-validation"></a>擴充 (BTS-XSD) 驗證
唯有當結構描述已經自訂了資料型別不同於 EDI 資料型別的元素時，EDI 接收管線和 EDI 傳送管線才會執行擴充驗證。 這些加入的元素不會由 EDI 驗證方法予以驗證，所以會納入擴充驗證範圍。 擴充驗證會使用 `System.Xml.XmlValidatingReader`，並會包括可在標準 XSD 中定義的所有檢查。  
  
 您可以為與某個合作對象往返的所有訊息設定擴充驗證。 這麼做即可**擴充驗證**中的核取方塊**驗證**頁面 (下**交易集設定**> 一節針對 X12 或 EDIFACT) 上在單向協議索引標籤**協議屬性** 對話方塊。 您可以啟用擴充驗證而不需要啟用 EDI 驗證，或者反之亦然。  
  
 擴充驗證是由下列檢查所組成：  
  
-   資料元素需求和允許的重複  
  
-   列舉型別  
  
-   資料元素長度驗證 (最小/最大)  
  
> [!IMPORTANT]
>  不支援延伸的驗證，EDI 傳送端批次訊息。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息驗證](../core/edi-message-validation.md)