---
title: 更新應用程式的重要考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating, applications
- applications, planning
- applications, updating
- planning, applications
- planning, updating
- updating, planning
ms.assetid: e7690bdf-943d-4bb6-b8cd-a6841b722d40
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24528dcce390376b7ac2e47199aa5ae06d412a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257742"
---
# <a name="important-considerations-for-updating-applications"></a>更新應用程式的重要考量
以下是在更新應用程式 (特別是在實際執行環境中執行的應用程式) 之前要考量的重要事項。  
  
## <a name="general-considerations"></a>一般考量  
  
-   群組領域可以看到合作對象和規則，所以加入額外的合作對象和規則可能會中斷其他應用程式。  
  
-   如果要解除部署其他成品所相依的成品，則必須先解除部署相依的成品。  
  
    > [!NOTE]
    >  BizTalk Server 管理主控台會顯示警告，以防止您以錯誤的順序解除部署成品：  
  
-   如果更新現有的應用程式中的 BizTalk 組件時，您可能需要重新啟動主控件執行個體，變更才會生效。 重新啟動主控件執行個體，就會停止所有其他主控件執行個體執行的應用程式。  
  
-   如果使用 Visual Studio 將應用程式部署到實際執行環境 (我們強烈建議您不要這麼做)，而在專案屬性中，將 [重新啟動主控件執行個體] 選項設定為 True，則在您部署應用程式時，所有的主控件執行個體都將重新啟動，包括未與此應用程式關聯的主控件執行個體。 這樣會停止在本機電腦的任何主控件執行個體上執行的所有其他應用程式。  
  
-   如果您想要更新已部署為 BizTalk 應用程式的 BizTalk Server 組件 (包含協調流程、結構描述或對應)，則可以執行下列任何一項：  
  
    -   執行並存部署。 一般只要遞增版本，就可以適當地修改較新的組件。 這樣讓兩個組件都會有相異完整組件名稱。 如需詳細資訊，請參閱[如何部署新版應用程式來執行的並行與現有版本](../core/deploy-new-application-version-to-run-side-by-side-with-existing-version.md)。  
  
    -   將現有的 BizTalk Server 組件以新的組件取代。 您必須停止所有可能會載入過時組件的主控件執行個體，並取代 GAC 中的過時組件，然後重新啟動主控件執行個體。  
  
-   如果要部署全新的應用程式以取代現有的應用程式，則必須修改其他應用程式與您要取代之應用程式間的所有參考。  
  
## <a name="considerations-for-updating-schemas"></a>更新結構描述的考量  
  
-   如果您將組件加入 BizTalk 群組中包含具有相同的訊息類型做為現有的結構描述的新結構描述的應用程式時，發生在管線中的結構描述解析時將使用具有最高的版本號碼的結構描述。 此外，如果一種訊息類型參考一個以上的.NET 型別，模稜兩可能導致管線執行失敗。 這是因為結構描述查閱會使用訊息類型、目標命名空間以及執行個體的根名稱。 在任何應用程式中，如果使用的結構描述具有與新結構描述相同的訊息類型，則管線都可能會發生這種狀況。 如需結構描述解析的詳細資訊，請參閱[管線元件中的結構描述解析](../core/schema-resolution-in-pipeline-components.md)。  
  
-   在更新結構描述時，也必須更新對應以參考結構描述 (或建立新對應) 以及任何依賴該結構描述的協調流程。  
  
-   如果要增加結構描述版本，則應該針對任何使用結構描述的管線執行個體和管線元件，更新結構描述的參考。  
  
-   解除部署結構描述會導致舊版結構描述成為作用中 (如果有)。  
  
## <a name="considerations-for-updating-policies"></a>更新原則的考量  
  
-   BizTalk Server 執行階段會使用已部署狀態的最新版原則。  
  
## <a name="see-also"></a>另請參閱  
 [更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)