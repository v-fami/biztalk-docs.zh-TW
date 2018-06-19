---
title: 升級和版本的應用程式的策略 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e881def2-c407-4205-a6b3-5c1fa5144bb4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf239b00d45d62a0ee3587baaea40482bfe50667
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015349"
---
# <a name="upgrading-and-versioning-strategies-for-applications"></a>升級和應用程式的版本控制方法
當您需要執行兩個版本的 BizTalk 方案的並存，或如果您無法使用 BizTalk 應用程式停機時間，來部署新的版本，BizTalk 應用程式版本可能會造成問題。 如果您不需要執行兩個版本的方案同時 （例如，您有任何長時間執行的協調流程），而服務維護視窗可用，然後是完全可接受的解除部署舊的版本，並部署新的版本做為版本控制策略 （沒有組件版本控制）。 這是可能的版本控制策略，不過我們還是建議遞增檔案版本號碼 (讓您知道哪一個版本執行的電腦上部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)])。  
  
## <a name="when-to-use-versioning"></a>使用版本控制的時機  
 如果您需要支援長時間執行的協調流程，和/或您需要執行 BizTalk 應用程式部署包含無 BizTalk 應用程式停機時間，則您必須實作並練習實線、 端對端[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]版本控制策略不同的版本控制案例。 這包括.NET 組件版本控制和版本控制的所有的 BizTalk 成品，其中包含結構描述、 對應、 管線、 管線元件、 協調流程、 自訂配接器、 自訂類別中呼叫的協調流程、 對應、 商務規則與 BAM。  
  
 結構描述版本控制中是唯一的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管線會判斷目標命名空間加上的根節點為基礎的訊息的訊息類型的結構描述中定義的名稱。 如需詳細資訊，請參閱[管線元件中的結構描述解析](../core/schema-resolution-in-pipeline-components.md)。 如果您需要版本您的結構描述，版本指標必須是目標命名空間的一部分。 變更結構描述版本連帶影響整個方案，並因此應該事先規劃。 在建立協調流程訊息時，搜尋**BizTalk Server: 8 的秘訣和訣竅更好的 BizTalk 程式設計**(提示 1： 一律使用多部分訊息類型)。 使用這個方法提供更大的彈性時結構描述版本。  
  
## <a name="using-factoring-for-assembly-versioning"></a>使用組件版本控制的建構  
 如果您需要支援長時間執行的協調流程、-並存部署或無停機時間升級，您應該實作的組件版本控制和封裝策略。 若要執行的 BizTalk 成品的組件版本控制，您的 BizTalk 方案組件需要中分解出來 （封裝） 的方式以允許[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]版本控制。  有三種類型的建構：  
  
-   **沒有建構**  
  
     所有的 BizTalk 成品是在一個組件。 這是容易了解和部署，但可提供最大的彈性。  
  
-   **完整的建構**  
  
     每個 BizTalk 成品是在它自己組件中。 這會提供最大的彈性，但最為複雜部署並了解。  
  
-   **最佳建構**  
  
     某處介於 「 沒有分解 」 及 「 完整分解 」 為基礎的 BizTalk 應用程式的深入分析。 除了版本控制，這可讓您輕鬆地實作您的 BizTalk 主控件設計。 藉由尋找 BizTalk 成品之間的關聯性來達到此目的。 成品一律版本一起通常可以放在相同的組件中。 如果需要之成品的獨立版本設定，然後將它們必須放在不同的組件中。 這是層級想要達到的建構。  
  
## <a name="additional-resources"></a>其他資源  
  
 定義和練習以確保它會提供任何並存的部署策略，您可能需要的實心版本控制策略。 BizTalk Server 應用程式的升級和版本控制策略的資源包括下列各項：  
  
-   [更新應用程式](../technical-guides/updating-an-application.md)  
  
-   [更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)
  
-   [BizTalk Server 專案版本管理](../core/biztalk-server-project-versioning.md)  
  
-   [了解 BizTalk Server 應用程式部署](../core/understanding-biztalk-application-deployment-and-management.md)


  
## <a name="see-also"></a>另請參閱  
 [檢查清單：設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)
