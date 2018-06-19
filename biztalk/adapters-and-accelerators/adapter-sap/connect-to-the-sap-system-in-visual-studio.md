---
title: 連接到 Visual Studio 中的 SAP 系統 |Microsoft 文件
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
ms.openlocfilehash: 20cd25c327f2081fed61e19e1571b91a0e39f556
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22217782"
---
# <a name="connect-to-the-sap-system-in-visual-studio"></a>連接到 Visual Studio 中的 SAP 系統
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
-   **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 用於 BizTalk Server 專案。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需開發使用 BizTalk Server 解決方案的詳細資訊，請參閱[開發 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
-   **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 用於 BizTalk Server 專案。 您使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需開發使用 BizTalk Server 解決方案的詳細資訊，請參閱[開發 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
    > [!NOTE]
    >  因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開為 WCF 自訂繫結和做為 BizTalk 配接器，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]從 BizTalk 專案連接至 SAP 系統。  
  
-   **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** 用於非 BizTalk 開發專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端類別或 WCF 服務的回呼介面，當您開發使用 WCF 服務模型的解決方案。 如需有關開發 WCF 服務模型的方案的詳細資訊，請參閱[開發 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。  
  
 若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]您必須先連接至 SAP 系統。 所有的三個使用者介面會出現的對話方塊，您可以透過此設定的連接來設定下列：  
  
-   **連接參數**。 這些是參數，可用來建置連接 URI，例如應用程式伺服器的主機或訊息伺服器主機，以及用戶端識別碼。  
  
-   **SAP 系統的使用者名稱密碼認證**。 這些用來建立連線時讓您驗證在 SAP 系統上。 您必須指定使用者名稱和密碼。  
  
-   **繫結屬性**。 繫結屬性是選擇性的您是否指定取決於主要是否您需要設定特定的繫結屬性的作業為目標。 例如，ReceiveIdoc 作業則必須設定**ReceiveIdocFormat**屬性繫結至字串。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
 最小值，當您設定連接至 SAP 系統，您只需要指定繫結內容和需要的連線，並會影響所傳回的中繼資料的連接參數[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]作業您要當做目標。 不過，您也可以指定任何其他繫結屬性與將在執行階段使用的連接參數的值。 這是因為：  
  
-   [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]繫結屬性和您指定當您設定的連接，並將這個檔案加入專案的連接參數建立 BizTalk 連接埠繫結檔案。  
  
-   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]從繫結屬性和您指定當您設定的連接，並將這個檔案加入您的專案目錄中的連接屬性，建立 app.config 檔案。  
  

  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)