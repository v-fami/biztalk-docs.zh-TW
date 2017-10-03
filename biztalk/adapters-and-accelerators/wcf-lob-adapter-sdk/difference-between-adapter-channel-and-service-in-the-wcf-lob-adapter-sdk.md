---
title: "配接器通道與服務之間的差異在 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24d41d96-0ea1-4a97-bd45-b65afdbbd923
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e377568887d3d626e288fc47f82714b189d44b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="difference-between-adapter-channel-and-service-in-the-wcf-lob-adapter-sdk"></a>WCF LOB 配接器 SDK 中配接器通道與服務之間的差異
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]各提供一組 Api，可用來公開 （expose） 來取用應用程式在相同電腦上或網路上的應用程式功能。 若要選擇最適當的架構，您必須考慮的目標系統應用程式公開功能的商務需求以及要公開的屬性。 本主題提供可讓您選擇適當的架構指導方針。  
  
## <a name="when-to-write-an-adapter"></a>當撰寫配接器  
 請考慮撰寫配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]時：  
  
-   目標系統是現有的非*Web 服務啟用*系統  
  
-   目標系統是動態的且可以增強使用新的作業  
  
-   目標系統有大量的中繼資料  
  
-   沒有大型、 不同的使用者數目的目標系統的資料  
  
-   消費性應用程式需要豐富的應用程式中繼資料探索功能  
  
 例如，如果目標系統包含數百個作業，以管理醫療保健宣告，而這些作業有動態 （表示使用者可以加入新的作業，執行額外的工作），是合理公開此功能使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. 這可確保新的作業是使用配接器的應用程式可探索。 與[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，您必須修改服務合約，因為它是靜態。  
  
## <a name="when-to-write-a-service"></a>當撰寫的服務  
 使用*WCF 服務模型*建立服務時：  
  
-   目標系統是靜態的有一組固定的作業  
  
-   目標系統有少量或沒有中繼資料  
  
-   服務開發人員深入瞭解要公開 (expose) 的應用程式  
  
-   會公開新的應用程式  
  
-   您要建立泛型傳輸配接器  
  
 比方說，如果目標系統包含 20 管理的運動團體的作業，您可以公開做為靜態合約使用作業[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。 如此一來，您可以避免不必要的中繼資料功能的實作，您可能可以減少開發時間。  
  
## <a name="when-to-write-a-channel"></a>當寫入通道  
 使用*WCF 通道模型*來建立通道時：  
  
-   建立網路通訊協定。 網路通訊協定的範例包括 WS-SECURITY 與 Ws-reliablemessaging 通訊協定。  
  
-   傳送/以外的 WCF （TCP、 HTTP、 具名管道、 MSMQ 與 PeerChannel） 中包含的傳輸接收 WCF 訊息。 例如，您可以撰寫 UDP 傳輸、 TIBCO 或 Java 訊息服務 (JMS) 傳輸。  
  
-   與並未公開為 Web 服務系統的整合。  在此情況下您的傳輸會做為調整現有的系統訊息格式或 API，可讓 WCF 用戶端直接與現有的系統通訊的 WCF 訊息的配接器。 這個範例是 Web 服務增強功能 (WSE) 3.0 TCP 傳輸。  
  
## <a name="see-also"></a>另請參閱  
 [計劃和設計配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [了解 LOB 系統與 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)