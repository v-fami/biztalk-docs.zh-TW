---
title: 連接到 Visual Studio 中的 SAP 系統 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAP system, connecting to
- Add Adapter Service Reference Visual Studio Plug-in
- Consume Adapter Service BizTalk Project Add-in
ms.assetid: 5fc356b1-05e8-4235-bb04-5ef6192c5291
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93acb23887eb173f924d21668077454718aa0145
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982903"
---
# <a name="connect-to-the-sap-system-in-visual-studio"></a>連接到 Visual Studio 中的 SAP 系統
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
- **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 位於 BizTalk Server 專案。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關如何使用 BizTalk Server 開發解決方案的詳細資訊，請參閱 <<c0> [ 開發的 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
- **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 位於 BizTalk Server 專案。 您使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關如何使用 BizTalk Server 開發解決方案的詳細資訊，請參閱 <<c0> [ 開發的 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
  > [!NOTE]
  >  因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開為 WCF 自訂繫結和 BizTalk 配接器，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]從連接到 SAP 系統的 BizTalk 專案。  
  
- **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** 用於非 BizTalk 的程式設計專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來開發使用 WCF 服務模型的方案時，產生 WCF 用戶端類別或 WCF 服務的回呼介面。 如需有關如何使用 WCF 服務模型開發解決方案的詳細資訊，請參閱 <<c0> [ 開發的 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
  若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]您必須先連接到 SAP 系統。 所有的三個使用者介面會顯示的對話方塊，您可以透過此設定的連接來設定下列：  
  
- **連接參數**。 這些是參數用來建置連接 URI，例如應用程式伺服器的主機或訊息伺服器主機，以及用戶端識別碼。  
  
- **SAP 系統的使用者名稱密碼認證**。 這些用來驗證您的 SAP 系統上建立連線時。 您必須指定使用者名稱和密碼。  
  
- **繫結屬性**。 繫結屬性是選擇性的您是否指定主要取決於是否您目標需要設定特定的繫結屬性的作業。 例如，針對 ReceiveIdoc 作業您必須設定**ReceiveIdocFormat**屬性繫結至字串。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
  最小值，當您設定連線到 SAP 系統中，您只需要指定繫結屬性和連接參數，才能建立連線，以及影響所傳回的中繼資料[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]作業您做為目標。 不過，您也可以指定任何其他繫結屬性與將在執行階段使用的連接參數的值。 這是因為：  
  
- [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從您指定當您設定的連接，並將此檔案加入至您專案的連接參數與繫結屬性建立 BizTalk 連接埠繫結檔案。  
  
- [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]從您指定當您設定的連接，並將此檔案加入您的專案目錄中的連接屬性與繫結屬性建立 app.config 檔案。  
  

  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)