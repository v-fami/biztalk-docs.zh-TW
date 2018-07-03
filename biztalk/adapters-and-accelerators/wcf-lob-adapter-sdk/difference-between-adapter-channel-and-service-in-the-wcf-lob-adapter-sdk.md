---
title: 配接器通道與服務之間的差異在 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24d41d96-0ea1-4a97-bd45-b65afdbbd923
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8583b615e6a6e8fcd999e5120bca531d3c74090d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010031"
---
# <a name="difference-between-adapter-channel-and-service-in-the-wcf-lob-adapter-sdk"></a>配接器通道與服務之間的差異在 WCF LOB 配接器 SDK
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]各提供一組可用來公開 （expose） 至取用端應用程式在相同電腦上或網路上的應用程式功能的 Api。 若要選擇最適當的架構，您必須考慮目標系統應用程式公開功能的商務需求以及要公開的屬性。 本主題提供可供您選擇適當的架構指導方針。  
  
## <a name="when-to-write-an-adapter"></a>撰寫配接器的時機  
 請考慮撰寫配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]時：  
  
- 目標系統是現有的非*Web 服務啟用*系統  
  
- 目標系統是動態的且皆可使用新的作業  
  
- 目標系統有大量的中繼資料  
  
- 大量、 多元化的目標系統的資料的使用者數目  
  
- 取用端應用程式需要豐富的應用程式中繼資料探索功能  
  
  例如，如果目標系統包含數百個用於管理健康照護理賠，作業，而且作業是動態的 （表示使用者可以加入新的作業，執行額外的工作），是合理來公開此功能，使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. 這可確保新的作業是使用配接器的應用程式設定為可探索。 使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，您必須修改服務合約，因為它是靜態。  
  
## <a name="when-to-write-a-service"></a>撰寫服務的時機  
 使用*WCF 服務模型*來建立服務時：  
  
- 目標系統是靜態的有一組固定的作業  
  
- 目標系統有少量或沒有中繼資料  
  
- 服務開發人員能夠深入瞭解要公開的應用程式  
  
- 公開全新的應用程式  
  
- 您要建立泛用的傳輸配接器  
  
  比方說，如果目標系統包含用於管理的運動團體 20 的作業，您可以將作業公開為靜態合約使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。 如此一來，您避免不必要的中繼資料功能的實作，以及您可能可以減少開發時間。  
  
## <a name="when-to-write-a-channel"></a>撰寫通道的時機  
 使用*WCF 通道模型*來建立通道時：  
  
-   建立網路通訊協定。 網路通訊協定的範例包括 WS-ReliableMessaging 通訊協定。  
  
-   傳送/以外的 WCF （TCP、 HTTP、 具名管道、 MSMQ 和 PeerChannel） 中包含的傳輸接收 WCF 訊息。 例如，您可以撰寫 UDP 傳輸、 TIBCO 或 Java 訊息服務 (JMS) 傳輸。  
  
-   不會公開為 Web 服務的系統整合。  在此情況下您的傳輸會做為調整現有系統的訊息格式或 API，可讓 WCF 用戶端直接與現有的系統通訊的 WCF 訊息的配接器。 這個範例是 Web 服務加強 (WSE) 3.0 TCP 傳輸。  
  
## <a name="see-also"></a>另請參閱  
 [規劃和設計配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [了解 LOB 系統與 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)