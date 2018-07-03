---
title: 連接至 Siebel 系統在 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add Adapter Service Reference Plug-in
- Consume Adapter Service Add-in
- how to, connect to the Siebel System in Visual Studio
ms.assetid: 4a94bce9-fda9-4e00-b26c-08672a80e3be
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 064382776201ec6772cc4864c153731ab8c11989
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999735"
---
# <a name="connect-to-the-siebel-system-in-visual-studio"></a>連接到 Visual Studio 中的 Siebel 系統
本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
- **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，並已安裝的一部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關使用開發解決方案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 使用 Siebel 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)。  
  
- **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，並已安裝的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝。 您使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關使用開發解決方案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 使用 Siebel 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)。  
  
  > [!NOTE]
  >  因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開為 WCF 自訂繫結和 BizTalk 配接器，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]從連接至 Siebel 系統的 BizTalk 專案。  
  
- **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** 用於非 BizTalk 的程式設計專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來開發使用 WCF 服務模型的方案時，產生 WCF 用戶端類別或 WCF 服務的回呼介面。 如需有關如何使用 WCF 服務模型開發解決方案的詳細資訊，請參閱 <<c0> [ 開發的 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)。  
  
  若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，您必須先連接至 Siebel 系統。 這三種方式呈現一個對話方塊，您可以透過此設定的連接來設定下列所示：  
  
- **連接參數**。 這些是用來建立連線 URI 名稱例如 Siebel 企業伺服器的參數。  
  
- **針對 Siebel 系統的使用者名稱密碼認證**。 這些用來登入驗證 Siebel 系統建立連線時。 您必須指定使用者名稱和密碼。  
  
- **繫結屬性**。 繫結屬性是選擇性的您是否指定主要取決於是否您目標需要設定特定的繫結屬性的作業。  
  
  最小值，當您設定連接至 Siebel 系統中，您只需要指定繫結屬性和連接參數，才能建立連線，以及影響所傳回的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]作業您做為目標。 不過，您也可以指定任何其他繫結屬性與將在執行階段使用的連接參數的值。 這是因為：  
  
- [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從您指定當您設定的連接，並將此檔案加入至您專案的連接參數與繫結屬性建立 BizTalk 連接埠繫結檔案。  
  
- [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]從您指定當您設定的連接，並將此檔案加入您的專案目錄中的連接屬性與繫結屬性建立 app.config 檔案。  
  
 
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)