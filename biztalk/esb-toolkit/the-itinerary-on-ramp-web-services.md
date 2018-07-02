---
title: 路線入口 Web 服務 |Microsoft Docs
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
ms.openlocfilehash: 04e0f30d93514fded12d20a06d9fa27fbcd632bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980711"
---
# <a name="the-itinerary-on-ramp-web-services"></a>路線入口 Web 服務
路線入口匝公開的方法，可讓用戶端將訊息提交以處理路線服務，然後邁向目標 Microsoft BizTalk 或 ESB 作業路線 Web 服務。  
  
 路線 Web 服務則傳遞承載 ESB 路線的管線元件，讓驗證以確認這些服務會定義在路線[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]組態。 然後元件會將特殊的內容屬性加入至包含已驗證的路線的訊息。  
  
 如果泛型路線匝道，是在郵件提交時未提供包含路線的 SOAP 標頭。 因此，ESB 路線選取器管線元件代替 ESB 路線管線元件。 ESB 路線選取器管線元件會解析路線，根據預先定義的解析程式的連接字串，並提供相同 ESB 路線管線元件所提供的驗證。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含兩種變化的路線服務以支援單向和要求-回應訊息交換模式。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含 ASP.NET (ASMX) 和 Windows Communication Foundation (WCF) 版本的這兩種服務，並提供泛型版本的 WCF 服務。  
  
 提供單向的路線服務的名稱是**ESB。ItineraryService**， **ESB。ItineraryServices.WCF**，和**ESB。ItineraryServices.Generic.WCF**。  
  
 提供雙向的路線服務的名稱是**ESB。ItineraryServices.Response**， **ESB。ItineraryServices.Response.WCF**，和**ESB。ItineraryServices.Generic.Response.WCF**。  
  
 每個行程 Web 服務會公開下列方法：  
  
- **SubmitRequest**。 Asmx 服務，這個方法會採用的執行個體**XmlNode**類別，其中包含要提交的訊息。 WCF 型服務，此方法會採用 XML 字串，其中包含要提交的訊息。  
  
- **SubmitRequestResponse**。 Asmx 服務，這個方法會採用的執行個體的參考**XmlNode**類別，包含要提交的訊息，並傳回回應訊息中的執行個體**XmlNode**傳遞至它。 WCF 型服務，這個方法會參考**物件**類型，它是 XML 字串，包含要提交的訊息，而且傳回的陣列**XmlNodes**在**物件**傳遞給它。  
  
  如需使用路線 Web 服務的詳細資訊，請參閱[安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。  
  
> [!NOTE]
>  根據預設，路線 Web 服務未設定為需要 Secure Sockets Layer (SSL) 用戶端存取時。 您應該以要求 SSL 用戶端存取和保護 Internet Information Services (IIS) Web 服務主機電腦和裝載使用網路層級 IPSec ESBExceptions 資料庫的伺服器之間的連線，並適當的服務設定檔案層級存取控制清單 (ACL) 權限。