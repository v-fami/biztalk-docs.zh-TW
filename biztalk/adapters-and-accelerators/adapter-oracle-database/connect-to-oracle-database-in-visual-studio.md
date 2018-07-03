---
title: 連接到 Visual Studio 中的 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 766264c8-bb3f-49e9-b851-1022d1fa5076
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 999c7b369f20bf0871e1150ddddd8dff977afa35
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013897"
---
# <a name="connect-to-oracle-database-in-visual-studio"></a>連接到 Visual Studio 中的 Oracle 資料庫
如何使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  

## <a name="connection-options-in-visual-studio"></a>Visual Studio 中的連接選項

當使用[!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]，有幾個選項可用來連接到 Oracle 資料庫。 這些選項包括： 

- **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關如何使用 BizTalk Server 開發解決方案的詳細資訊，請參閱 <<c0> [ 使用 Oracle 資料庫配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)。  
  
- **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** 位於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。 您使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關如何使用 BizTalk Server 開發解決方案的詳細資訊，請參閱 <<c0> [ 使用 Oracle 資料庫配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)。  
  
  > [!NOTE]
  >  因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開為 WCF 自訂繫結和 BizTalk 配接器，您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]從 BizTalk 專案，以連接到 SQL Server。  
  
- **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** 用於非 BizTalk 的程式設計專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來開發使用 WCF 服務模型的方案時，產生 WCF 用戶端類別或 WCF 服務的回呼介面。 如需有關如何使用 WCF 服務模型開發解決方案的詳細資訊，請參閱 <<c0> [ 開發的 Oracle 資料庫應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)。  
  
  若要使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您必須先連接到 Oracle 資料庫。 這三種方式呈現一個對話方塊，您可以透過此設定的連接來設定下列所示：  
  
- **連接參數**。 這些是用來建立連線 URI 的參數。 您必須指定資料來源 （Oracle net 的服務名稱）。  
  
- **Oracle 資料庫的使用者名稱密碼認證**。 這些用來驗證您的 Oracle 資料庫上建立連線時。 您必須指定使用者名稱和密碼。  
  
- **繫結屬性**。 產生作業的中繼資料時，繫結屬性是在設計階段，也就是選擇性的。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
  最小值，當您設定連線到 Oracle 資料庫中，您只需要指定繫結屬性和連接參數，才能建立連線，以及影響所傳回的中繼資料[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]作業您想要為目標。 不過，您也可以指定任何其他繫結屬性與將在執行階段使用的連接參數的值。 這是因為：  
  
- [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]從您指定當您設定連線，連線參數與繫結屬性建立 BizTalk 連接埠繫結檔案，並將此檔案加入至您的專案。 稍後，您可以使用此繫結檔案建立在連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需有關繫結檔案的詳細資訊，請參閱[設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
- [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]從您指定當您設定連線，連接屬性與繫結屬性建立 app.config 檔案，並將此檔案加入您的專案目錄中。  
  

  
## <a name="see-also"></a>另請參閱  
[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)