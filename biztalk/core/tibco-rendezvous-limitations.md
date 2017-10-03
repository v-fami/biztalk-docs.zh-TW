---
title: "TIBCO Rendezvous 限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TIBCO Rendezvous, limitations
ms.assetid: 8e210457-2887-43f9-a249-be1daa6ee4eb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717188e42450d13dee92364cd9c673aaaf48eaf6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-limitations"></a>TIBCO Rendezvous 限制
在 TIBCO Rendezvous 中，並不保證欄位名稱是唯一的。 如果 TIBCO Rendezvous 訊息包含兩個相同的欄位名稱，結果產生的 XML 會無效。  
  
 其他限制還包括：  
  
-   不會提供欄位排序。  
  
-   根據 TIBCO Rendezvous 文件，不可列印的字元不會使用在主體名稱中，但是，仍有使用這類字元的可能。 BizTalk Adapter for TIBCO Rendezvous 不支援含有這些字元的主體名稱。  
  
-   不支援對精靈的安全連線。  
  
-   不支援自訂資料型別。  
  
-   傳輸端不支援「認證傳訊」。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)