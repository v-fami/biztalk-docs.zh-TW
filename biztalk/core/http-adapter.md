---
title: "HTTP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, receive adapters
- HTTP adapters, send adapters
- HTTP adapters
- receive adapters, HTTP adapters
- send adapters, HTTP adapters
- HTTP adapters, about HTTP adapters
ms.assetid: a9423052-8392-4006-ab46-79834169c796
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d9be9fac6fdb65c4516c671b6c0e30096e83a27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter"></a>HTTP 配接器
您使用 HTTP 配接器在 Microsoft BizTalk Server 與使用 HTTP 通訊協定的應用程式之間交換資訊。 HTTP 是內部商務訊息交換的主要通訊協定。 應用程式可以藉由傳送 HTTP POST 或 HTTP GET 要求到指定的 HTTP URL 來傳送訊息到伺服器。 HTTP 配接器接收 HTTP 要求，然後提交到 BizTalk Server 進行處理。 同樣地，BizTalk Server 可以藉由傳送 HTTP POST 要求到指定的 HTTP URL 來傳輸訊息到遠端應用程式。  
  
 HTTP 配接器是由兩個配接器所組成—接收配接器和傳送配接器。 HTTP 接收配接器是 IIS 程序裝載的 Microsoft Internet Information Services (IIS) Internet Server Application Programming Interface (ISAPI) 延伸模組，控制使用 HTTP 配接器的接收位置。 HTTP 傳送配接器控制使用 HTTP 配接器的傳送埠。  
  
 本節討論 HTTP 接收配接器與 HTTP 傳送配接器兩者的工作流程與批次支援。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [HTTP 接收配接器](../core/http-receive-adapter.md)  
  
-   [HTTP 傳送配接器](../core/http-send-adapter.md)  
  
-   [設定 HTTP 配接器](../core/configuring-the-http-adapter.md)  
  
-   [HTTP 配接器安全性建議](../core/http-adapter-security-recommendations.md)