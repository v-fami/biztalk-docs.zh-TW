---
title: 若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing BizTalk applicatons, run-time tasks
- developing BizTalk applications, design-time tasks
ms.assetid: 76204181-18ad-43b5-b589-539aafd66835
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e457ec1eb3b3c79ef1fc1a4618bb6a0ef37755d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981967"
---
# <a name="building-blocks-to-create-biztalk-applications-with-the-siebel-adapter"></a>若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊
使用 Siebel 系統上執行的作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]牽涉到兩個一組活動： 設計階段活動和執行階段的活動。 若要使用執行 Siebel 系統上的作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須執行一組設計階段和執行階段使用的工作[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台分別。 本節提供這些工作的概觀。 中的所有主題本節中，示範如何執行特定作業上使用 Siebel 系統[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，會根據這些高層級的工作。  
  
## <a name="design-time-tasks"></a>設計階段工作  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供功能，以瀏覽、 搜尋及擷取 Siebel 中繼資料的商務元件和商務服務，使用 XML 結構描述定義語言 (Xsd) 的形式[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 Xsd 專屬於您想要在 Siebel 系統上執行的作業，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]功能只有當您建立 BizTalk 專案。 在設計階段，您可能需要執行下列工作。  
  
- **建立 BizTalk 專案，並產生結構描述**。 若要開始，您必須建立 BizTalk 專案，在 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並產生商業元件或商務服務，您將會叫用在 Siebel 系統的結構描述。 例如，如果您想要將記錄插入帳戶商務元件，您必須產生帳戶商務元件的插入作業的中繼資料。 在此步驟中使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述。 如需詳細資訊，請參閱 <<c0> [ 取得 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。  
  
- **設定協調流程**。 一旦您已經產生結構描述，則您必須使用 「 協調流程設計師設定協調流程。 基本的協調流程中，您可以新增傳送和接收圖形，以及傳送和接收邏輯連接埠。 在稍後步驟中，您將使用 BizTalk Server 管理主控台這些邏輯連接埠對應至實體連接埠。 協調流程會使用這些連接埠收取配接器用戶端所傳送的訊息。 協調流程接著會將訊息傳遞至 Siebel 系統。 一旦收到來自 Siebel 系統的回應，協調流程會將配接器用戶端的回應。  
  
- **建立訊息，並連結至結構描述**。 在您的協調流程中，您必須建立將會對應到您的第一個步驟中產生的結構描述的訊息。 一般而言，您會建立要求和回應訊息。 這些訊息會對應到相對應的要求和回應結構描述。  
  
- **對應至訊息和連接埠的 [訊息] 圖形**。 在您的協調流程中，您現在必須對應您在第二個步驟，您在第三個步驟中建立的訊息中加入每個圖形。 您也必須對應 「 訊息 」 圖形會傳送該訊息的連接埠。  
  
   比方說，如果您在協調流程中的第一個圖形將會收到一則訊息 「 接收 」 圖形，您將對應此圖形到 「 要求 」 訊息，傳送要求訊息的連接埠。  
  
- **建置和部署 BizTalk 專案**。 您已設定 協調流程，並對應訊息、 連接埠，以及結構描述之後，您必須建置 BizTalk 方案。 建置專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您將需要組件金鑰檔案。 您已成功建置方案之後，您必須部署該方案。  
  
  > [!NOTE]
  >  詳細描述這些高層級的工作，包括程序資訊不遵循的主題提供。  
  
  一旦部署方案後，會完成您的設計階段工作。 現在，您必須執行的執行的階段工作。  
  
## <a name="run-time-tasks"></a>執行階段工作  
  
- **設定應用程式**。 您在設計階段部署的 BizTalk 專案會顯示在 BizTalk Server 管理主控台中為協調流程。 您必須設定此協調流程，藉由對應您在設計階段，您現在必須建立使用 BizTalk Server 管理主控台的實體連接埠所建立的邏輯連接埠。  
  
   實體的通訊埠，您必須指定 「 動作 」 或 「 動作對應 」。 此動作會對應至您想要在 Siebel 系統上執行的作業。 您需要設定動作，如果您不想要使用動態的動作。 
  
- **啟動應用程式**。 設定應用程式之後，您必須啟動應用程式，並在定義的檔案位置卸除輸入的訊息。 協調流程會取用輸入的訊息並將它們傳送至 Siebel 系統，並接收回應。 此回應會在另一個定義的檔案位置。  
  
  若要完成這些高層級的設計階段和執行階段工作，您也必須執行其他工作。 例如，當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述，您必須指定的連接來連接到 Siebel 系統的 URI。 本節提供資訊這類重複的工作，您必須執行您在開發 BizTalk 應用程式使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
