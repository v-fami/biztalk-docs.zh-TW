---
title: 互動配接器不可否認性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13fb77c-b10c-4f8a-ba4b-efecc83e092c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d7eabd7eab04c0bd64af0164b73b38af197ac9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224918"
---
# <a name="interact-adapter-non-repudiation"></a>互動配接器不可否認性
外寄 InterAct 訊息不可否認性支援被透過 SwInt:NRIndicator 設 SwInt:RequestControl 或 SwInt:ResponseControl，視需要為 TRUE。 這是必要只有當服務不會選取不可否認性支援，根據預設，根據服務的設定檔。  
  
 不可否認性根據之前的訊息傳輸所 SNL，建立有效的簽章。 因此，若要取得的傳出要求訊息的不可否認性支援，它會強制 SwInt:RequestCrypto 項目，內含 SwInt:RequestControl，在 SwInt:RequestControl 中設定為 TRUE。  
  
 回應訊息的需求是相等的不同之處在於 SwInt:ResponseControl; 內所包含的項目是 SwInt:ResponseCryptoSwInt:ResponseCrypto 必須設定為 TRUE。  
  
 如需有關的要求不可否認性支援，就必須以涵蓋 SwInt:RequestHeader、 SwInt:RequestPayload 及的 SwInt:RequestDescriptor SwInt:SwiftRequestRef 的訊息簽章。 SwInt:SwiftRequestRef 會由 SWIFTNet 連結自動產生。 與連接產生 SwInt:SwiftRequestRef，SNL 也會自動調整 SwSec:MemberRef 內的值來產生必要的訊息簽章 SwSec:CryptoControl。 同樣地，如需有關回應非 repudiatin 支援，則必須以涵蓋 SwInt:ResponseHeader、 SwInt:ResponsePayload 及的 SwInt:ResponseDescriptor SwInt:SwiftResponseRef 的訊息簽章。 SwInt:SwiftResponseRef 會由 SWIFTNet 連結自動產生。 與連接產生 SwInt:SwiftResponseRef，SNL 也會自動調整 SwSec:MemberRef 內的值來產生必要的訊息簽章 SwSec:CryptoControl。  
  
 商務服務設定檔選取不可否認性，根據預設，如果必要的訊息簽章是否仍需要選取 （只中所述，SwInt:RequestControl 或 SwInt:ResponseControl），並在訊息離開必須先選取SNL。  
  
 如果根據商務服務設定檔的特徵選取會叫用的訊息時，在不可否認性支援，而且所需的簽章找不到具有訊息，訊息將會拒絕的參數。 將傳回狀態例外狀況訊息，訊息的寄件者。  
  
 找不到與不可否認性支援一致的裝載加密。 如果訊息選取不可否認性支援，且內容已加密之全部或部分，訊息將會拒絕的 SWIFTNet 連結。  
  
 請注意，如果服務不需要不可否認功能、 要求或回應，指出在控制項中，不可否認性將會遭到拒絕。  
  
## <a name="see-also"></a>另請參閱  
 [互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)