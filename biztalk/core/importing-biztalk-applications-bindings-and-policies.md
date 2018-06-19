---
title: 匯入 BizTalk 應用程式、 繫結和原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- importing, applications
- importing, policies
- applications, importing
- policies, importing
- importing, bindings
- bindings, importing
ms.assetid: 678bdb03-efaa-4053-9048-b71fc539d191
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18f7ea348fb34f4f8cc08e748799dcf8368a3c35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256774"
---
# <a name="importing-biztalk-applications-bindings-and-policies"></a>匯入 BizTalk 應用程式、繫結和原則
本節中的主題說明如何將 BizTalk 應用程式、繫結和原則匯入至 BizTalk 群組或應用程式中。 中所述[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)，匯出應用程式會建立您可以再使用應用程式的成品匯入到不同的 BizTalk 群組中的應用程式的 Windows Installer (.msi) 檔案。 如果群組中沒有您指定匯入的應用程式，則會建立此應用程式。 此外，也會註冊應用程式的成品，並且將其資料儲存在群組的 BizTalk 資料庫。 如需詳細資訊，請參閱[什麼發生時匯入成品](../core/what-happens-when-artifacts-are-imported.md)。  
  
 您也可以匯入到 BizTalk 群組或應用程式，從 BizTalk 群組、 應用程式或組件，您匯出的繫結中所述[匯出繫結](../core/exporting-bindings6.md)。 匯入繫結時，會覆寫 BizTalk 群組、應用程式或組件中任何同名的現有繫結。  
  
 此外，您可以匯入原則到您的 BizTalk 群組或應用程式，從匯出的 BizTalk 群組中所述[如何匯出原則](../core/how-to-export-a-policy.md)。 新群組中的應用程式就可以使用此原則。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)  
  
-   [匯入繫結](../core/importing-bindings2.md)  
  
-   [如何匯入原則](../core/how-to-import-a-policy.md)