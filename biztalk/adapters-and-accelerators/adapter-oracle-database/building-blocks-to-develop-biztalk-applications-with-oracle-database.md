---
title: 開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing, BizTalk applications
- run-time tasks
- design-time tasks
ms.assetid: ad9ca856-5569-41ab-8617-ae6db5e3b4d7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0747569ef58e1f2223baefba6c51b77b205eb0d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214838"
---
# <a name="building-blocks-to-develop-biztalk-applications-with-oracle-database"></a>開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊
執行 Oracle 資料庫上的作業使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]牽涉到兩組工作： 設計階段和執行階段。  
  
## <a name="design-time-tasks"></a>設計階段工作  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供功能，以瀏覽、 搜尋及擷取 Oracle 的中繼資料資料表、 預存程序和其他這類項目中的 XML 結構描述定義語言 (Xsd) 的形式使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。 Xsd 專屬於您想要在 Oracle 資料庫上執行的操作。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]可僅當您建立 BizTalk 專案。 在設計階段，您需要執行下列工作：  
  
-   **建立 BizTalk 專案，並產生結構描述**。 您必須建立 BizTalk 專案，在 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並產生將 Oracle 資料庫執行作業的結構描述。 例如，如果您想要將記錄插入員工資料表，您必須產生 EMPLOYEE 資料表的插入作業的中繼資料。 在此步驟中，您會使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 如需詳細資訊，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。
  
-   **設定協調流程**。 一旦您已經產生結構描述，則您必須使用 「 協調流程設計師 」 設定協調流程。 基本協調流程中，您可以新增傳送和接收圖形以及傳送和接收邏輯連接埠。 在稍後步驟中，您將對應這些邏輯連接埠至實體連接埠使用 BizTalk Server 管理主控台。 協調流程會使用這些連接埠挑選配接器用戶端傳送的訊息。 協調流程接著會將訊息傳遞到 Oracle 資料庫。 一旦收到回應時，從 Oracle 資料庫，協調流程會傳遞至配接器用戶端的回應。  
  
-   **建立訊息並連結到結構描述**。 在您的協調流程中，您必須建立會對應到您在第一個步驟中產生的結構描述的訊息。 通常，您會建立要求訊息和回應訊息。 這些訊息會對應至相對應的要求和回應結構描述。  
  
-   **對應至訊息和連接埠的 [訊息] 圖形**。 在您的協調流程，您現在必須對應每個訊息，您在第三個步驟中建立第二個步驟中所加入的圖形。 您也必須對應 「 訊息 」 圖形至將會傳送該訊息的連接埠。  
  
     比方說，如果將會收到一則訊息 「 接收 」 圖形在協調流程中的第一個圖形，請要求訊息並傳送要求訊息的連接埠對應此圖形。  
  
-   **建置和部署 BizTalk 專案**。 您設定協調流程和對應的訊息、 連接埠和結構描述之後，您必須建置 BizTalk 方案。 建置專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您需要的組件金鑰檔案。 在您成功建置方案之後，您必須部署該方案。  
  
    > [!NOTE]
    >  本章節的各種主題提供的更詳細的描述，這些高階的工作，包括程序資訊。  
  
 一旦部署方案時，會完成您設計階段的工作。 現在，您必須執行的執行階段工作。  
  
## <a name="run-time-tasks"></a>執行階段工作  
 在執行階段，您可以使用 BizTalk Server 管理主控台來部署和監視您在設計階段建立的協調流程。 此外，您必須：  
  
-   **設定應用程式**。 您在設計階段部署的 BizTalk 專案會出現在 BizTalk Server 管理主控台中做為協調流程。 您必須設定此協調流程透過對應您在設計階段，您現在必須建立使用 BizTalk Server 管理主控台的實體連接埠所建立的邏輯連接埠。  
  
     實體連接埠，您必須指定 「 動作 」 或 「 動作對應 」。 這個動作會對應至您想要在 Oracle 資料庫上執行的操作。 您要設定的動作，如果您不想要使用動態的動作。  
  
-   **啟動應用程式**。 設定應用程式之後，您必須啟動應用程式，拖放輸入的訊息已定義的檔案位置。 協調流程取用輸入的訊息，並將其傳遞到 Oracle 資料庫並接收回應。 此回應會是可供您使用其他定義的檔案位置。  
  
 若要完成這些高層級的設計階段和執行階段工作，您也必須執行其他工作。 例如，當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生結構描述，您必須指定 URI 要連接到 Oracle 資料庫的連接。 本節提供資訊在這種重複的工作，您必須執行在開發 BizTalk 應用程式使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  

  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)