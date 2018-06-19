---
title: 若要建立的 SAP 應用程式的建置組塊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- design-time tasks
- run-time tasks
- developing, fundamentals of (BizTalk applications)
ms.assetid: 591a5597-5e7d-44b0-8bee-e1c987c5e6c3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d507518b61b3c61b1815ec3ffe94bc1df5603d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218166"
---
# <a name="building-blocks-to-create-sap-applications"></a>若要建立的 SAP 應用程式的建置組塊
對 SAP 系統使用執行作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]牽涉到兩個一組活動： 設計階段活動和執行階段活動。 若要使用執行 SAP 系統上的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須執行一組使用的設計階段和執行階段工作[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台分別。 本節提供這些工作的概觀。 中的所有主題本節中，可示範如何執行 SAP 系統使用的特定作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，這些高階的工作建立模型。  
  
## <a name="design-time-tasks"></a>設計階段工作  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供功能，以瀏覽、 搜尋和擷取 Rfc、 Bapi，和使用 XML 結構描述定義語言 (Xsd) 的表單中的 Idoc 的 SAP 中繼資料[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 Xsd 專屬於您想要在 SAP 系統上，執行作業和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]可僅當您建立 BizTalk 專案。 在設計階段，您需要執行下列工作。  
  
-   **建立 BizTalk 專案，並產生結構描述**。 開始使用，您必須建立 BizTalk 專案，在 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和的 RFC，您將會叫用 SAP 系統中產生的結構描述。 比方說，如果您想要叫用 RFC_CUSTOMER_GET，SAP 系統中，您必須針對 RFC_CUSTOMER_GET 產生中繼資料。 在此步驟使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述。 如需詳細資訊，請參閱[取得 Visual Studio 中的 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)。  
  
-   **設定協調流程**。 一旦您已經產生結構描述，則您必須使用 「 協調流程設計師 」 設定協調流程。 基本協調流程中，您可以新增傳送和接收圖形以及傳送和接收邏輯連接埠。 在稍後步驟中，您將對應這些邏輯連接埠至實體連接埠使用 BizTalk Server 管理主控台。 協調流程會使用這些連接埠挑選配接器用戶端傳送的訊息。 協調流程接著會將訊息傳遞至 SAP 系統。 一旦從 SAP 系統接收回應，協調流程會傳遞至配接器用戶端的回應。  
  
-   **建立訊息並連結到結構描述**。 在您的協調流程中，您必須建立會對應到您在第一個步驟中產生的結構描述的訊息。 通常，您會建立要求訊息和回應訊息。 這些訊息會對應至相對應的要求和回應結構描述。  
  
-   **對應至訊息和連接埠的 [訊息] 圖形**。 在您的協調流程現在必須對應至您在第三個步驟中建立的訊息第二個步驟中加入每個圖形。 您也必須對應 「 訊息 」 圖形至將會傳送該訊息的連接埠。  
  
     例如，如果收到訊息 「 接收 」 圖形在協調流程中的第一個圖形，您對應此圖形到要求訊息和連接埠傳送要求訊息。  
  
-   **建置和部署 BizTalk 專案**。 您已設定協調流程，並對應訊息、 連接埠，以及結構描述之後，您必須建置 BizTalk 方案。 建置專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您將需要組件金鑰檔案。 在您成功建置方案之後，您必須部署該方案。  
  
    > [!NOTE]
    >  本章節的各種主題提供的更詳細的描述，這些高階的工作，包括程序資訊。  
  
 一旦部署方案時，會完成您設計階段的工作。 現在，您必須執行的執行階段工作。  
  
## <a name="run-time-tasks"></a>執行階段工作  
 在執行階段，您可以使用 BizTalk Server 管理主控台來部署和監視您在設計階段建立的協調流程。 此外，您必須：  
  
-   **設定應用程式**。 您在設計階段部署的 BizTalk 專案會出現在 BizTalk Server 管理主控台中做為協調流程。 您必須設定此協調流程會對應至實體連接埠，您現在必須建立使用設計階段建立的邏輯連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
     實體連接埠，您必須指定 「 動作 」 或 「 動作對應 」。 這個動作會對應至您想要在 SAP 系統上執行的操作。 您要設定的動作，如果您不想要使用動態的動作。 
  
-   **啟動應用程式**。 設定應用程式之後，您必須啟動應用程式，拖放輸入的訊息已定義的檔案位置。 協調流程取用輸入的訊息並將其傳遞至 SAP 系統，並接收回應。 此回應會是可供您使用其他定義的檔案位置。  
  
 若要完成這些高層級的設計階段和執行階段工作，您也必須執行其他工作。 例如，當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述，您必須指定的連接來連接到 SAP 系統的 URI。 本節提供資訊在這種重複的工作，您必須執行在開發 BizTalk 應用程式使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [新增 SAP 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)  
  
-   [設定 SAP 配接器的連線 URI](../../adapters-and-accelerators/adapter-sap/configure-the-connection-uri-for-the-sap-adapter.md)  
  
-   [設定登入 SAP 系統的認證](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md) 
  
-   [設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)
  
-   [設定 SAP 系統的 SOAP 動作](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md)
  
-   [以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)
  
-   [設定使用連接埠繫結檔案至 SAP 的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)
  
-   [SAP 配接器中設定動態連接埠](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md)
  
-   [重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 SAP 配接器](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)