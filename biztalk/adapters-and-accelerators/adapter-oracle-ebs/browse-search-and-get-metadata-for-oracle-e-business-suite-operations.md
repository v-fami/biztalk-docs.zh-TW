---
title: 瀏覽、 搜尋，並取得中繼資料的 Oracle E-business Suite 作業 |Microsoft 文件
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
ms.openlocfilehash: a26b13ddef6efe9214e7d889d5d8e02d2f1505cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217790"
---
# <a name="browse-search-and-get-metadata-for-oracle-e-business-suite-operations"></a>瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 使用這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件，您可以：  
  
-   瀏覽作業，以擷取中繼資料。  
  
-   搜尋作業來擷取中繼資料。  
  
-   加入選取的作業的訊息結構描述和連接埠繫結的組態檔來[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
-   WCF 用戶端類別或選取的作業和組態檔 (app.config) 的 WCF 服務合約 （介面） 的非 BizTalk 程式設計專案時加入使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="how-is-the-metadata-categorized"></a>如何為中繼資料分類？  
 [!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可讓您連接到 Oracle E-business Suite 伺服器中可用之成品的三種不同檢視，**應用程式為基礎的檢視**，**成品為基礎的檢視**，而**結構描述為基礎的檢視**。 為什麼需要三種不同檢視成品的同一組？ 下表列出您為什麼您的理由使用特定的檢視。  
  
|檢視|當您使用它|  
|----------|------------------------|  
|**應用程式為基礎的檢視**|此檢視會由 Oracle E-business Suite 應用程式名稱來分類。 當您知道哪一個應用程式包含您想要使用的成品時，請使用此檢視。|  
|**成品為基礎的檢視**|此檢視是由 Oracle E-business Suite 成品分類。 當您知道哪一個 Oracle E-business Suite 成品，您想要搭配運作，但您不確定哪個應用程式所屬的成品時，請使用此檢視。 使用此檢視，您可以搜尋特定的成品 Oracle E-business Suite 的所有應用程式。<br /><br /> 成品為基礎的檢視也列出基礎的 Oracle 資料庫，例如 PL-SQL Api、 資料表、 檢視、 函數和程序中的成品。 這些成品會根據其所屬的結構描述，進一步分類。 因此，另一個使用成品為基礎的檢視表是使用隸屬於您的結構描述的成品以及成品屬於其他結構描述。 此檢視也可讓您跨所有結構描述中搜尋成品。|  
|**結構描述為基礎的檢視**|此檢視會以基礎的 Oracle 資料庫中可用的結構描述分類。 當您知道哪一個結構描述具有您想要使用的成品時，請使用此檢視。 在此檢視中，如分類為 PL-SQL Api、 程序、 函數、 資料表和檢視表的成品。|  
  
 如需有關 Oracle E-business Suite 成品的分類方式的詳細資訊，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中使用 新增配接器中繼資料精靈](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md)的組織中的成品的另一個主要原因不同的檢視是要搜尋特定的成品。 如需有關如何搜尋成品的詳細資訊，請參閱[搜尋 Oracle E-business Suite 作業](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md)。  
  
> [!IMPORTANT]
>  節點顯示依據連接您在建立連接時指定的 URI。 如果您指定 Oracle E-business Suite 成品沒有權限的認證，則無法使用中的成品**應用程式為基礎的檢視**。 此外，**成品為基礎的檢視**不會列出屬於 Oracle E-business Suite 的成品。  
  

  
## <a name="see-also"></a>另請參閱  
 [取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)