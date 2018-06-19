---
title: 連接到 Visual Studio 中的 Oracle E-business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e290ea7e-03f3-49d4-9f18-1e539d727d9c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b9221914a9f58c3f739eefd5f07986b0105f77e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216814"
---
# <a name="connect-to-the-oracle-e-business-suite-in-visual-studio"></a>連接到 Oracle E-business Suite，Visual Studio 中
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
-    **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需開發使用 BizTalk Server 解決方案的詳細資訊，請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。  
  
-    **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。 您使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需開發使用 BizTalk Server 解決方案的詳細資訊，請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。  
  
    > [!NOTE]
    >  因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開為 WCF 自訂繫結和做為 BizTalk 配接器，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]從 BizTalk 專案連接到 Oracle E-business Suite。  
  
-    **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** 用於非 BizTalk 開發專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端類別或 WCF 服務的回呼介面，當您開發使用 WCF 服務模型的解決方案。 如需有關開發 WCF 服務模型的方案的詳細資訊，請參閱[開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)。  
  
 若要使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您必須先連接到 Oracle E-business Suite 的資訊。 這三個方法會顯示的對話方塊，您可以透過此設定的連接來設定下列：  
  
-   **連接參數**。 這些是用來建置連線 URI 的參數。 您必須指定資料來源 (Oracle net service name)。  
  
-   **使用者名稱密碼認證 for Oracle E-business Suite**。 這些用來建立連線時讓您驗證 Oracle E-business suite。 您必須指定使用者名稱和密碼。  
  
    > [!IMPORTANT]
    >  在這個階段，您可以指定 Oracle E-business Suite 為基礎的 Oracle 資料庫的認證。 連線並產生中繼資料中，您可以指定任何認證。 不過，當執行作業，以叫用 Oracle E-business Suite 成品，您必須指定 Oracle E-business Suite 認證因為需要它們來設定您想要叫用 Oracle E-business Suite 應用程式的應用程式內容。 如需有關設定應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
-   **繫結屬性**。 產生作業的中繼資料時，繫結屬性是在設計階段，也就是選擇性的。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
 最小值，當您設定連接到 Oracle 資料庫中，您只需要指定繫結內容和需要的連線，並會影響所傳回的中繼資料的連接參數[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]作業您想要為目標。 不過，您也可以指定任何其他繫結屬性與將在執行階段使用的連接參數的值。 這是因為：  
  
-   [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]繫結屬性和您指定當您設定連接的連接參數建立 BizTalk 連接埠繫結檔案，並將這個檔案加入至您的專案。 稍後，您可以使用此繫結檔案建立在連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需繫結檔案的詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
-   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]繫結屬性和連接屬性時設定此連接時，指定建立 app.config 檔案，並將這個檔案加入專案目錄中。  
  

-   [連接到 Oracle E-business Suite，在 Visual Studio 中使用 新增配接器服務參考外掛程式](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-service-reference.md)  
  
## <a name="see-also"></a>另請參閱  
 [取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)