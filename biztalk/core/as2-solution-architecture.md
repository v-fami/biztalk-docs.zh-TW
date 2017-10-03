---
title: "AS2 方案架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41e493ba-919b-4520-9c12-92d6757984ef
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c22557059bd13dd99e0b24a2291b7f121d561bbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-solution-architecture"></a>AS2 方案架構
AS2 處理與 EDI 處理是分開的。 AS2 訊息的接收、處理和通知傳送，都是與 EDI 內容的處理分開。 因此，AS2 處理的設計和設定都與 EDI 處理分開進行。 此外，您可以使用 AS2 傳輸 EDI 訊息或非 EDI 訊息。  
  
 本章節描述 AS2 方案的架構上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，包括端對端、 接收端和傳送端處理。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [AS2 傳訊](../core/as2-messaging.md)  
  
-   [中協議的 AS2 處理的角色](../core/the-role-of-agreements-in-as2-processing.md)  
  
-   [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)  
  
-   [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)