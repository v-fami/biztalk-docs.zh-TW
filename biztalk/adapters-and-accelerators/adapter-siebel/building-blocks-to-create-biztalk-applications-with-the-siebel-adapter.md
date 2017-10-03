---
title: "若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing BizTalk applicatons, run-time tasks
- developing BizTalk applications, design-time tasks
ms.assetid: 76204181-18ad-43b5-b589-539aafd66835
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dea8fc354c3187ef7613ac35850b9408a05a9c0e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="building-blocks-to-create-biztalk-applications-with-the-siebel-adapter"></a>若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊
使用 Siebel 系統上執行的作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]牽涉到兩個一組活動： 設計階段活動和執行階段活動。 若要使用執行 Siebel 系統上的作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須執行一組使用的設計階段和執行階段工作[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台分別。 本節提供這些工作的概觀。 中的所有主題本節中，可示範如何執行特定作業上使用 Siebel 系統[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，這些高階的工作建立模型。  
  
## <a name="design-time-tasks"></a>設計階段工作  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供功能，以瀏覽、 搜尋及擷取 Siebel 中繼資料的商務元件和商務服務 中使用 XML 結構描述定義語言 (Xsd) 的形式[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 Xsd 專屬於您想要在 Siebel 系統上執行的操作和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]可僅當您建立 BizTalk 專案。 在設計階段，您可能需要執行下列工作。  
  
-   **建立 BizTalk 專案，並產生結構描述**。 開始使用，您必須建立 BizTalk 專案，在 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並產生結構描述以取得商務元件的商務服務，您將會叫用 Siebel 系統中。 例如，如果您想要將記錄插入帳戶商務元件，您必須產生帳戶商務元件的插入作業的中繼資料。 在此步驟使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述。 如需詳細資訊，請參閱[取得 Visual Studio 中的 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。  
  
-   **設定協調流程**。 一旦您已經產生結構描述，則您必須使用 「 協調流程設計師 」 設定協調流程。 基本協調流程中，您可以新增傳送和接收圖形以及傳送和接收邏輯連接埠。 在接下來的步驟，您將使用 BizTalk Server 管理主控台這些邏輯連接埠對應至實體連接埠。 協調流程會使用這些連接埠收取配接器用戶端所傳送的訊息。 協調流程接著會將訊息傳遞至 Siebel 系統。 一旦收到來自 Siebel 系統的回應時，協調流程會傳遞至配接器用戶端的回應。  
  
-   **建立訊息並連結到結構描述**。 在您的協調流程中，您必須建立會對應到您在第一個步驟中產生的結構描述的訊息。 一般而言，您會建立要求和回應訊息。 這些訊息會對應至相對應的要求和回應結構描述。  
  
-   **對應至訊息和連接埠的 [訊息] 圖形**。 在您的協調流程現在必須對應至您在第三個步驟中建立的訊息第二個步驟中加入每個圖形。 您也必須對應 「 訊息 」 圖形至將會傳送該訊息的連接埠。  
  
     例如，如果將會收到一則訊息 「 接收 」 圖形在協調流程中的第一個圖形，您將對應此圖形到 「 要求 」 訊息，傳送要求訊息的連接埠。  
  
-   **建置和部署 BizTalk 專案**。 您已設定協調流程，並對應訊息、 連接埠，以及結構描述之後，您必須建置 BizTalk 方案。 建置專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您將需要組件金鑰檔案。 在您成功建置方案之後，您必須部署該方案。  
  
    > [!NOTE]
    >  詳細描述這些高層級的工作，包括程序資訊會提供下節的主題。  
  
 一旦部署方案時，會完成您的設計階段工作。 現在，您必須執行的執行的階段工作。  
  
## <a name="run-time-tasks"></a>執行階段工作  
  
-   **設定應用程式**。 您在設計階段部署的 BizTalk 專案會顯示在 BizTalk Server 管理主控台中為協調流程。 您必須設定此協調流程透過對應您在設計階段，您現在必須建立使用 BizTalk Server 管理主控台的實體連接埠所建立的邏輯連接埠。  
  
     實體連接埠，您必須指定 「 動作 」 或 「 動作對應 」。 這個動作會對應至您想要在 Siebel 系統上執行的操作。 您要設定的動作，如果您不想要使用動態的動作。 
  
-   **啟動應用程式**。 設定應用程式之後，您必須啟動應用程式，拖放輸入的訊息已定義的檔案位置。 協調流程取用輸入的訊息，並將其傳遞至 Siebel 系統並接收回應。 此回應會是可供您使用其他定義的檔案位置。  
  
 若要完成這些高層級的設計階段和執行階段工作，您也必須執行其他工作。 例如，當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述，您必須指定連接至 Siebel 系統連接 URI。 本節提供資訊在這種重複的工作，您必須執行在開發 BizTalk 應用程式使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
