---
title: 若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fac7cbf4-b111-43ad-8726-36d037918c9c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96095b0d0b7df8dfabee1ff2a1955008bd757182
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975487"
---
# <a name="building-blocks-to-develop-biztalk-applications-with-the-sql-adapter"></a>若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊
若要使用執行 SQL Server 上的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須執行一組使用的設計階段和執行階段工作[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台分別。 本節提供這些工作的概觀。 中的所有主題本節中，示範如何執行 SQL Server 使用的特定作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，會根據這些高層級的工作。  
  
## <a name="using-visual-studio"></a>使用 Visual Studio  
  
1. **建立 BizTalk 專案，並產生結構描述**。 您必須建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，和您將 SQL Server 執行的作業產生結構描述。 例如，如果您想要將記錄插入 SQL Server 資料表中，您必須產生該資料表的插入作業的結構描述。 若要產生結構描述，您必須使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。  
  
2. **設定協調流程**。 一旦您已經產生結構描述，則您必須使用 「 協調流程設計師設定協調流程。 基本的協調流程中，您可以新增傳送和接收圖形，以及傳送和接收邏輯連接埠。 在稍後步驟中，您對應這些邏輯連接埠至實體連接埠使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 協調流程會使用這些連接埠挑選配接器用戶端傳送的訊息。 協調流程接著會將訊息傳遞至 SQL Server。 一旦 SQL Server 會傳送回應，協調流程會將回應傳回給配接器用戶端。  
  
3. **建立訊息，並連結至結構描述**。 在您的協調流程中，您必須建立將會對應到您的第一個步驟中產生的結構描述的訊息。 一般而言，您會建立要求訊息和回應訊息。 這些訊息會對應到相對應的要求和回應結構描述。  
  
4. **對應至訊息和連接埠的 [訊息] 圖形**。 在您的協調流程中，您現在必須對應您在第二個步驟，您在第三個步驟中建立的訊息中加入每個圖形。 您也必須對應 「 訊息 」 圖形會傳送該訊息的連接埠。  
  
    比方說，如果將會收到一則訊息 「 接收 」 圖形的協調流程中的第一個圖形，請要求訊息並傳送要求訊息的連接埠對應此圖形。  
  
5. **建置和部署 BizTalk 專案**。 您已設定協調流程和對應的訊息、 連接埠和結構描述之後，您必須建置 BizTalk 方案。 建置專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您需要的組件金鑰檔案。 您已成功建置方案之後，您必須部署該方案。  
  
> [!NOTE]
>  本節的各種主題提供這些高層級的工作，包括程序的詳細資訊，更詳細的描述。  
  
 一旦您已成功建置並部署 BizTalk 專案，您的工作中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]來完成。 現在，您必須執行某些工作使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. **設定應用程式**。 使用您部署的 BizTalk 專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]會顯示在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]為協調流程的管理主控台。 您必須設定此協調流程，藉由對應您在中建立的邏輯連接埠[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]您現在必須建立使用的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
    實體的通訊埠，您必須指定 「 動作 」 或 「 動作對應 」。 此動作會對應至您想要在 SQL Server 上執行的作業。 您需要指定的動作，如果您不想要使用動態的動作。 如需有關動作的詳細資訊，請參閱[設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。  
  
2. **啟動應用程式**。 設定應用程式之後，您必須啟動應用程式，並放置在定義的檔案位置的要求訊息。 協調流程會使用要求訊息、 將它們傳遞給 SQL Server，並接收回應。 此回應是配接器用戶端可用的其他定義的檔案位置。  
  
   若要完成這些高層級的工作，您也必須執行其他工作。 例如，當您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述，您必須指定的連接來連接到 SQL Server 的 URI。 本節提供資訊這類重複的工作，您必須執行您在開發 BizTalk 應用程式使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [將 SQL 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)  
  
-   [設定 SQL 配接器的連線 URI](../../adapters-and-accelerators/adapter-sql/configure-the-connection-uri-for-the-sql-adapter.md)  
  
-   [設定登入認證，SQL 配接器](../../adapters-and-accelerators/adapter-sql/configure-the-sign-in-credentials-for-the-sql-adapter.md)
  
-   [設定 SQL 配接器的繫結屬性 ](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md) 
  
-   [設定 SQL 配接器的 SOAP 動作 ](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)
  
-   [手動設定 SQL 配接器的實體連接埠繫結 ](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md) 
  
-   [設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)
  
-   [設定動態連接埠](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)
  
-   [重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)