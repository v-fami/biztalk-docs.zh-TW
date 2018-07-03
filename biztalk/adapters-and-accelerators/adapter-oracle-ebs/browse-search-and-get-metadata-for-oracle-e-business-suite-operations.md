---
title: 瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05a0656c-84d0-4f25-9571-90a9df587b8c
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46588632c4444c5c38966cfc22fd75711d2af11a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996879"
---
# <a name="browse-search-and-get-metadata-for-oracle-e-business-suite-operations"></a>瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]而[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 透過使用這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件，您可以：  
  
- 瀏覽作業，以擷取中繼資料。  
  
- 搜尋作業來擷取中繼資料。  
  
- 新增選取的作業的訊息結構描述和連接埠繫結的組態檔來[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
- 將 WCF 用戶端類別或選取的作業和組態檔 (app.config) 的 WCF 服務合約 （介面） 新增至非 BizTalk 的程式設計專案，當使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="how-is-the-metadata-categorized"></a>中繼資料的分類為何？  
 [!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可讓您連接到 Oracle E-business Suite 伺服器中可用的成品的三個不同的檢視 —**應用程式為基礎的檢視**，**成品為基礎的檢視**，而**結構描述為基礎的檢視**。 為何需要三個不同的檢視相同的成品集？ 下表列出的原因，您為什麼要使用特定的檢視。  
  
|檢視|當您使用它|  
|----------|------------------------|  
|**應用程式為基礎的檢視**|此檢視是由 Oracle E-business Suite 應用程式名稱來分類。 當您知道哪些應用程式包含您想要使用的成品時，請使用此檢視。|  
|**成品為基礎的檢視**|此檢視是由 Oracle E-business Suite 成品分類。 當您知道您想要使用的工作，但您的 Oracle E-business Suite 成品不確定哪個應用程式所屬的成品時，請使用此檢視。 使用此檢視，您可以搜尋特定成品 Oracle E-business Suite 的所有應用程式。<br /><br /> 成品為基礎的檢視也會列出基本的 Oracle 資料庫，例如 PL-SQL Api、 資料表、 檢視、 函數和程序中的成品。 這些成品會進一步分類根據其所屬的結構描述。 因此，另一個使用成品為基礎的檢視表是使用屬於您的結構描述的成品以及屬於其他結構描述的成品。 此檢視也可讓您跨所有結構描述中搜尋成品。|  
|**結構描述為基礎的檢視**|此檢視會依基礎的 Oracle 資料庫中可用的結構描述分類。 當您知道哪一個結構描述具有您想要使用的成品時，請使用此檢視。 在此檢視中，如分類為 PL-SQL Api、 程序、 函數、 資料表和檢視的成品。|  
  
 如需有關 Oracle E-business Suite 成品的分類方式的詳細資訊，請參閱[連接到 Visual Studio 中使用 新增配接器中繼資料精靈中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md)另一個組織中的成品的主要原因不同的檢視是可以輕鬆地搜尋特定的成品。 如需有關您可以搜尋成品的詳細資訊，請參閱 <<c0> [ 搜尋 Oracle E-business Suite 作業](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md)。  
  
> [!IMPORTANT]
>  節點顯示依據連接您在建立連接時指定的 URI。 如果您指定的 Oracle E-business Suite 構件沒有權限的認證時，您無法使用中的成品**應用程式為基礎的檢視**。 此外，**成品為基礎的檢視**不會列出屬於 Oracle E-business Suite 的成品。  
  

  
## <a name="see-also"></a>另請參閱  
 [取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)