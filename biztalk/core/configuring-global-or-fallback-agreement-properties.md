---
title: "設定全域或後援協議屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c375d03-6f22-4a67-9eac-d8896de2f7ee
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb693a17cad17eadaf0d005d12075dde30daa33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-global-or-fallback-agreement-properties"></a>設定全域或後援協議屬性
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 找不到可解析交換的協議時，就會使用後援協議屬性來處理訊息。 後援協議屬性不適用於已知道協議的情況，而且也不適用於任何或所有協議。  
  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到訊息時，它會嘗試比對協議的傳送者資訊與訊息中的傳送者資訊。 傳送者資訊位於 X12 訊息的 ISA5 和 ISA6 資料項目，以及 EDIFACT 的 UNB2.1 和 UNB 2.2 資料項目中。 協議資訊位於識別項中的索引標籤的單向協議索引標籤**協議屬性** 對話方塊。 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 找不到協議，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 就會使用後援協議屬性來決定命名空間、處理訊息以及傳送任何通知。  
  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送訊息時，EDI 傳送管線會透過比對訂閱 MessageBox 中 XML 訊息的傳送埠，以及與協議關聯的傳送埠，來判斷訊息解析目標的協議。 如果傳送埠未與任何協議關聯，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 就會使用後援協議屬性來處理訊息以進行傳送。  
  
> [!NOTE]
>  傳送埠關聯只是執行協議解析的其中一種方式。 如需外寄訊息的協議解析的詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定 X12 後援協議屬性](../core/configuring-x12-fallback-agreement-properties.md)  
  
-   [設定 EDIFACT 後援協議屬性](../core/configuring-edifact-fallback-agreement-properties.md)  
  
## <a name="see-also"></a>另請參閱  
 [中協議 EDI 處理的角色](../core/the-role-of-agreements-in-edi-processing.md)