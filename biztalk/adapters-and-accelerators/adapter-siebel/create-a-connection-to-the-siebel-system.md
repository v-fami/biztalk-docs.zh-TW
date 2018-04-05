---
title: 建立連接至 Siebel 系統 |Microsoft 文件
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
ms.openlocfilehash: a108335263e85db832f4db144d27b64b92429683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-the-siebel-system"></a>建立連接至 Siebel 系統
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓透過 WCF 端點位址的 Siebel 系統的通訊。 在 WCF 中的端點位址識別服務的網路位置，以及通常表示做為統一資源識別元 (URI)。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]表示這個位置做為連接 URI，其中包含屬性的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]用以連接至 Siebel 系統。 您必須指定連線 URI 時您：  
  
-   建立通道處理站或通道接聽程式使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。  
  
-   建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取訊息結構描述從[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
 此章節的主題描述如何之間建立連線[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]與藉由提供您與 Siebel 系統：  
  
-   連接屬性和結構的 Siebel 連線 URI 的相關資訊。  
  
-   示範如何建立連接所使用的主題連結[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  

  
## <a name="see-also"></a>另請參閱  
[開發 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)