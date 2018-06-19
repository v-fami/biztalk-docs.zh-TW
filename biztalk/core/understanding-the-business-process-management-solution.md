---
title: 了解商務程序管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solutions, resources
- process management solutions, applications
- process management solution tutorial, background information
- process management solutions, about process management solutions
- applications, process management solutions
ms.assetid: fa6ad8d2-08d7-4770-9394-835f99bfd146
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9759f6521297377b204f0695a511de40d22a830d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287902"
---
# <a name="understanding-the-business-process-management-solution"></a>瞭解商務程序管理解決方案
本節描述的解決方案會呈現一個實作商務程序管理應用程式的方法。 在理想的商務程序管理員中，代表商務程序之解決方案的部分 (商務規則、與特定後端系統通訊、傳送回應訊息)，會與支援程序的基礎結構分開。  
  
 在這個解決方案中，Southridge Video 的有線服務訂單系統，商務程序會分割成一連串的階段。 對於商務規則和後端系統一無所知的訂單管理員，會引導階段的作業。 訂單管理員會從訂單仲介接收訂單，而訂單仲介會將訂單引導至數位不同的訂單管理員。  
  
 這個解決方案充分利用了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的功能，並顯示了 (但不只是) 使用應用程式內部的訊息來協調應用程式的部分。  
  
## <a name="reader-guidance"></a>使用指南  
 這份文件假設您已熟悉 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 同時假設您也瞭解企業應用程式整合和 Web 服務的基本概念。  
  
 此外，若要閱讀和依照開發人員文件，您應該熟悉如何使用建置應用程式[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]且具有執行下列工作： 建立專案、 設定參考，以及偵錯和測試 BizTalk解決方案。  
  
## <a name="ordering-cable-service-from-southridge-video"></a>排序從 Southridge Video 的有線服務  
 商務程序管理解決方案會實作 Southridge Video 的有線服務訂購系統。 客戶撥打電話到服務中心，服務中心內會有客戶服務代表接收訂單並將之輸入訂單系統。 下圖顯示透過系統的一般訂單流程：  
  
 ![商務程序管理解決方案工作流程](../core/media/business-process-manager-solution-work-flow.gif "Business_Process_Manager_Solution_Work_Flow")  
  
 訂單會移至訂單仲介，訂單仲介會將訂單傳送到訂單管理員。 訂單管理員會以正確的順序來執行處理階段，以處理訂單。 請注意，有些類型的錯誤會移至作業中心以進行修正和重新提交，而解決方案會在 SQL Server 資料表中記錄每張訂單的歷程記錄。  
  
 下圖說明處理訂單之步驟的概要。  
  
 ![商務程序管理解決方案順序](../core/media/business-process-manager-solution-sequence.gif "Business_Process_Manager_Solution_Sequence")  
  
 請注意，訂單可以更新，也可以取消。  
  
## <a name="business-requirements"></a>商務需求  
 商務程序管理解決方案是 Southridge Video (有線服務提供者) 訂單系統的範例。 它會顯示一個在 Microsoft BizTalk Server 中實作程序管理員模式的方法。 這個解決方案會使用一個協調流程，透過實作商務程序的兩個附屬協調流程，來管理訂單流程。 這個結構來自解決方案的商務需求，其中包括下列項目：  
  
-   管理商務程序版本的能力  
  
-   處理長時間執行的訂單  
  
-   修改或取消仍在處理的訂單 (補充傳遞訂單)  
  
-   避免擱置訂單  
  
-   透過整個程序追蹤訂單  
  
-   批次訂單處理  
  
-   接收來自遠端資料中心的訂單  
  
-   允許不同群組處理訂單處理的部分  
  
-   藉由新增 BizTalk 群組來擴充應用程式  
  
-   透過遠端將訂單管理員公佈成應用程式伺服器  
  
 Southridge Video 的商務需求產生三部分結構： 訂單仲介、 程序管理員和商務程序本身。 Southridge Video 有兩個個別的 IT 群組會涉及此應用程式。 傳訊群組會維護企業傳訊基礎結構，並提供將應用程式連線至該基礎結構的元件。 另一個群組會寫入和維護特定商務程序的應用程式。 因此，訂單仲介會與訂單程序管理員和程序階段分開，如此即可由個別的群組來維護。 因為訂單仲介是個別的元件，所以它也可以擴充到仲介訂單，並傳到多個程序管理員。 可能會加入程序管理員以支援新的營業項目，像是 VIP 服務。  
  
 Southridge Video 訂單是長時間執行的處理序： 有線服務訂單可能需要從一分鐘到一年才能完成。 因為 BizTalk 協調流程的執行個體必須執行以完成，這表示協調流程執行個體的存留期間最多為一年。  
  
 Southridge Video 需要長時間執行程序的架構，該程序允許應用程式元件在訂單處理期間進行變更。 因此，Southridge 會將訂單處理分割成多個階段，如此一來即可使用最新的程序元件來完成訂單。 如需如何判斷階段界限商務程序中的資訊，請參閱[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。  
  
 訂單的長處理時間，在某種程度上也會判斷是否需要變更傳遞訂單。 修改訂單是解決方案包含大量中斷系統的原因之一。 這個中斷系統會在訂單完成之前，簡化訂單變更或取消作業。 這個解決方案會使用 .NET 訊息，在解決方案的功能部分之間進行通訊，以處理中斷。  
  
 因為系統有眾多外部相依性，特定作業可以在失敗後重試。 例如，若後端系統無法使用，而對其要求逾時，這個解決方案會等候適當的間隔並重試要求。 因為外部系統的連線是透過自訂程式碼，這部分的解決方案會廣泛使用 .NET 反映，以允許重試物件方法。  
  
 如同解決方案是以實際公司做為基礎一樣，它會假設訂單處理的問題可以由人員在作業群組中處理。 同理，部分類型的訂單錯誤將傳回給客戶服務代表參考，客戶服務代表可以取消或修正並重新提交訂單。  
  
## <a name="business-process-management-solution-resources"></a>商務程序管理解決方案資源  
 閱讀下列文件，以取得有關商務程序管理解決方案的其他資訊。  
  
### <a name="business-process-management-solution-resources"></a>商務程序管理解決方案資源  
  
-   [開發商務程序管理解決方案](../core/developing-a-business-process-management-solution.md)  
  
     開發人員與軟體設計師可以使用這本指南，為建置和執行商務程序管理應用程式所需的所有程式碼、模式、架構和效能設計問題提供相關文件。  
  
-   [部署商務程序管理解決方案](../core/deploying-the-business-process-management-solution.md)  
  
     對於 BizTalk 有基本認識的 IT 專業人員可以使用這本指南，來建置和執行商務程序管理應用程式。 本指南假設讀者對於應用程式如何在分散式環境中運作，已有基本的認識。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案](../core/business-process-management-solution.md)