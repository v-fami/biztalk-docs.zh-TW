---
title: 若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊 |Microsoft Docs
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
ms.openlocfilehash: 703bff35321fcedb4240d8ced1f422707c0ca51e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973799"
---
# <a name="building-blocks-to-develop-biztalk-applications-with-oracle-database"></a>若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊
使用中執行的 Oracle 資料庫的作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]牽涉到兩組工作： 設計階段和執行階段。  
  
## <a name="design-time-tasks"></a>設計階段工作  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供功能，以瀏覽、 搜尋及擷取 Oracle 的中繼資料資料表、 預存程序和其他這類項目中的 XML 結構描述定義語言 (Xsd) 的形式使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。 Xsd 專屬於您想要在 Oracle 資料庫上執行的作業。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]功能只有當您建立 BizTalk 專案。 在設計階段中，您需要執行下列工作：  
  
- **建立 BizTalk 專案，並產生結構描述**。 您必須在 Microsoft 中的 BizTalk 專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並產生將 Oracle 資料庫執行作業的結構描述。 例如，如果您想要將記錄插入員工資料表，您必須產生 EMPLOYEE 資料表的插入作業的中繼資料。 在此步驟中，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 如需詳細資訊，請參閱 <<c0> [ 取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。
  
- **設定協調流程**。 一旦您已經產生結構描述，則您必須使用 「 協調流程設計師設定協調流程。 基本的協調流程中，您可以新增傳送和接收圖形，以及傳送和接收邏輯連接埠。 在稍後步驟中，您對應這些邏輯連接埠至實體連接埠使用 BizTalk Server 管理主控台。 協調流程會使用這些連接埠挑選配接器用戶端傳送的訊息。 協調流程接著會將訊息傳遞到 Oracle 資料庫。 一旦收到回應時，從 Oracle 資料庫，協調流程會將配接器用戶端的回應。  
  
- **建立訊息，並連結至結構描述**。 在您的協調流程中，您必須建立將會對應到您的第一個步驟中產生的結構描述的訊息。 一般而言，您會建立要求訊息和回應訊息。 這些訊息會對應到相對應的要求和回應結構描述。  
  
- **對應至訊息和連接埠的 [訊息] 圖形**。 在您的協調流程中，您現在必須對應您在第二個步驟，您在第三個步驟中建立的訊息中加入每個圖形。 您也必須對應 「 訊息 」 圖形會傳送該訊息的連接埠。  
  
   比方說，如果將會收到一則訊息 「 接收 」 圖形的協調流程中的第一個圖形，請要求訊息並傳送要求訊息的連接埠對應此圖形。  
  
- **建置和部署 BizTalk 專案**。 您已設定協調流程和對應的訊息、 連接埠和結構描述之後，您必須建置 BizTalk 方案。 建置專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您需要的組件金鑰檔案。 您已成功建置方案之後，您必須部署該方案。  
  
  > [!NOTE]
  >  本節的各種主題提供這些高層級的工作，包括程序的詳細資訊，更詳細的描述。  
  
  一旦部署方案後，會完成您的設計階段工作。 現在，您必須執行的執行階段工作。  
  
## <a name="run-time-tasks"></a>執行階段工作  
 在執行階段，您可以使用 BizTalk Server 管理主控台，來部署及監視您在設計階段建立的協調流程。 此外，您必須：  
  
- **設定應用程式**。 您在設計階段部署的 BizTalk 專案會顯示在 BizTalk Server 管理主控台中為協調流程。 您必須設定此協調流程，藉由對應您在設計階段，您現在必須建立使用 BizTalk Server 管理主控台的實體連接埠所建立的邏輯連接埠。  
  
   實體的通訊埠，您必須指定 「 動作 」 或 「 動作對應 」。 此動作會對應至您想要在 Oracle 資料庫上執行的作業。 您需要設定動作，如果您不想要使用動態的動作。  
  
- **啟動應用程式**。 設定應用程式之後，您必須啟動應用程式，並在定義的檔案位置卸除輸入的訊息。 協調流程會取用輸入的訊息並將它們傳送到 Oracle 資料庫，並接收回應。 此回應會在另一個定義的檔案位置。  
  
  若要完成這些高層級的設計階段和執行階段工作，您也必須執行其他工作。 例如，當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生結構描述，您必須指定的連接來連接到 Oracle 資料庫的 URI。 本節提供資訊這類重複的工作，您必須執行您在開發 BizTalk 應用程式使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  

  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)