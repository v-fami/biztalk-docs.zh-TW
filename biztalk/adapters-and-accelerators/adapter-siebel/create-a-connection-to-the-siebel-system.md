---
title: 建立 Siebel 系統的連線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connecting, to the Siebel system
ms.assetid: 5810eeb1-6e26-4620-a731-fb352eebea2e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7710d25528cadff3d082fc067f951830f2bb8efe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013111"
---
# <a name="create-a-connection-to-the-siebel-system"></a>建立 Siebel 系統的連線
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓透過 WCF 端點位址的 Siebel 系統的通訊。 在 WCF 中的端點位址會識別服務的網路位置，而且通常表示做為統一資源識別元 (URI)。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]表示此位置做為連線 URI，其中包含屬性的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]用以連接到 Siebel 系統。 您必須指定 URI 的連接時您：  
  
- 建立通道處理站或通道接聽程式，使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。  
  
- 建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。  
  
- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來擷取從訊息結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
  在本節中的主題描述如何之間建立連線[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]與 Siebel 系統藉由提供您使用：  
  
- 連接屬性和 Siebel 連線 URI 的結構資訊。  
  
- 示範如何建立連接所使用的主題連結[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  

  
## <a name="see-also"></a>另請參閱  
[開發您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)