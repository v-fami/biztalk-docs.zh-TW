---
title: 開發 BizTalk 應用程式使用 Siebel 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 08/02/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk applications, developing
- developing, BizTalk applications
- CBR
- Content-Based Routing
ms.assetid: 1a2a9765-305c-44b2-aed7-5437725e4c19
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8267c07027d9994b0115ebaf49fde96e76f2716
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221926"
---
# <a name="develop-biztalk-applications-using-the-siebel-adapter"></a>開發 BizTalk 應用程式使用 Siebel 配接器

## <a name="overview"></a>概觀
建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生 XML 結構描述。 一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合產生結構描述的訊息。  
  
 CBR 可用在案例中傳送到 Siebel 系統的訊息不需要任何大量的處理。 比方說，如果您知道接收埠會接收僅特定類型的訊息，您可以加入篩選條件要比對篩選條件運算式至傳送埠將訊息路由傳送埠。  
  
 在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 本節提供使用 BizTalk 協調流程使用 Siebel 系統上執行作業的相關資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，能夠與 WCF 繫結互動。  

## <a name="before-you-begin"></a>開始之前  

* 若要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，一律將**EnableBizTalkCompatibilityMode**內容繫結至**True**。 如需步驟，請參閱[siebel 設定繫結屬性](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md)。
  
* [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]自動未列在 BizTalk Server 管理主控台。 這是因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]是 WCF 自訂繫結。 

* 產生中繼資料，請使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。 請勿使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 如需使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱[取得 Visual Studio 中的 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。   

  
## <a name="see-also"></a>另請參閱  
[開發 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)