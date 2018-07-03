---
title: Siebel 配接器支援哪些作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, performing by using the adapter
ms.assetid: 800cf44b-357f-4850-8878-f49ceb549adf
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3f080cedb74210d02806681b6c9e20656d3d09e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004775"
---
# <a name="what-operations-are-supported-by-the-siebel-adapter"></a>Siebel 配接器支援哪些作業
配接器用戶端可以透過下列方式執行 Siebel 系統上的作業：  
  
- 建立 BizTalk 專案。  
  
- 使用 WCF 通道模型。  
  
- 使用 WCF 服務模型。  
  
  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開應用程式，可以在其上叫用並，它可以依次叫用應用程式上的作業。 這些作業會叫用透過通道傳送 SOAP 訊息。 如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。 訊息結構和每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)。  
  
  本節提供有關 Siebel 系統使用支援的作業資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
> [!NOTE]
>  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援從 Siebel 系統接收傳入的呼叫。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [在 Siebel 商務元件上的作業](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)  
  
-   [在 Siebel 商務服務的相關作業](../../adapters-and-accelerators/adapter-siebel/operations-on-business-services-in-siebel.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Siebel eBusiness Applications 概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)