---
title: "EDI 解決方案架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55709a89-7706-4c64-ada3-16951951c943
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42afbb604a8cef1387418e175a39150f0182c607
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-solution-architecture"></a>EDI 解決方案架構
「電子資料交換」(EDI) 是商務實體以電子方式交換資料的最普遍方法之一。 EDI 的使用限定訊息語法和標準 （包括 ANSI X12 和 UN/EDIFACT），傳訊通訊協定和傳輸。 以下是 EDI 傳訊的特性：  
  
-   EDI 傳訊通訊協定可確保資料一定會如預期般抵達，並且會自動偵測和報告損毀或不正確的資料。  
  
-   EDI 機制通常會指定資料彙總方式 (批次處理)。  
  
-   使用者通常會以實作 EDI 指導方針子集或特定實作的方式，自訂 EDI 文件定義。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用可剖析和序列化 EDI 訊息的 EDI 專屬接收和傳送管線來處理 EDI 訊息。 本節描述 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 EDI 解決方案架構，包括接收端和傳送端處理的細節、訊息驗證和狀態報告。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [EDI 傳訊](../core/edi-messaging.md)  
  
-   [中協議 EDI 處理的角色](../core/the-role-of-agreements-in-edi-processing.md)  
  
-   [BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)  
  
-   [BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)  
  
-   [EDI 訊息驗證](../core/edi-message-validation.md)  
  
-   [使用 XML 工具延伸模組](../core/using-the-xml-tool-extensions.md)