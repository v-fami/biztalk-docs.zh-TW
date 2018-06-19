---
title: 路線上手 Web Services |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7551974-b9d2-4ae3-b54c-3aa5ba058e95
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36d3724a6cd57dca8157c05e95d9e196f0fb6cf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295430"
---
# <a name="the-itinerary-on-ramp-web-services"></a>路線上手 Web 服務
路線上手，公開的方法，可讓用戶端將訊息提交以處理路線服務，然後向前目標 Microsoft BizTalk 或 ESB 作業路線 Web 服務。  
  
 行程 Web 服務給裝載 ESB 行程管線元件中，會驗證以確認這些服務會定義在路線[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]組態。 然後元件會將特殊的內容屬性加入至包含已驗證的行程的訊息。  
  
 在泛型路線上手，訊息提交期間未提供 SOAP 標頭包含路線。 同理，ESB 行程選取器管線元件用來取代 ESB 行程管線元件。 ESB 行程選取器管線元件會解析路線根據預先定義的解析程式的連接字串，並提供相同 ESB 行程管線元件所提供的驗證。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含路線服務來支援單向和要求-回應訊息交換模式的兩種變化。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含 ASP.NET (ASMX) 和 Windows Communication Foundation (WCF) 版本的這兩項服務，並提供泛型版本的 WCF 服務。  
  
 提供的單向路線服務的名稱是**ESB。ItineraryService**， **ESB。ItineraryServices.WCF**，和**ESB。ItineraryServices.Generic.WCF**。  
  
 提供雙向的路線服務的名稱是**ESB。ItineraryServices.Response**， **ESB。ItineraryServices.Response.WCF**，和**ESB。ItineraryServices.Generic.Response.WCF**。  
  
 每個行程 Web 服務會公開下列方法：  
  
-   **SubmitRequest**。 Asmx 服務，這個方法會採用的執行個體**XmlNode**類別，其中包含要提交的訊息。 WCF 型服務，這個方法會採用 XML 字串，其中包含要提交的訊息。  
  
-   **SubmitRequestResponse**。 Asmx 服務，這個方法會採用的執行個體的參考**XmlNode**類別，其中包含要提交的訊息，並傳回回應訊息執行個體中**XmlNode**傳遞至它。 WCF 型服務，這個方法會採用參考**物件**類型，它是 XML 字串，其中包含要提交的訊息，並傳回陣列**XmlNodes**中**物件**傳遞給它。  
  
 如需使用路線 Web 服務的詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。  
  
> [!NOTE]
>  根據預設，路線 Web 服務不會設定為需要安全通訊端層 (SSL) 用戶端存取時。 您應該設定為要求 SSL 用戶端存取和保護網際網路資訊服務 (IIS) Web 服務主機電腦和裝載使用網路層級 IPSec ESBExceptions 資料庫的伺服器之間的連線並適當的服務檔案層級存取控制清單 (ACL) 權限。