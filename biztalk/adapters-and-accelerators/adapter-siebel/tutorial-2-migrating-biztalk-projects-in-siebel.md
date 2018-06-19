---
title: 教學課程 2： Siebel 中的移轉 BizTalk 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a2a1828-8cc8-4b80-99bd-c083c04e5d04
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b8d138d348e750102d82a4aba2e39bc7d119c8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223006"
---
# <a name="tutorial-2-migrating-biztalk-projects-in-siebel"></a>教學課程 2： 移轉 Siebel 中的 BizTalk 專案
Siebel 配接器隨附於 Microsoft BizTalk Server 的先前版本不同於 WCF 基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在許多方面，包括：  
  
-   建立 BizTalk 專案的設計階段經驗。  
  
-   中繼資料擷取的經驗。  
  
-   結構描述檔案名稱和命名空間。  
  
-   資料類型對應。  
  
-   可以使用配接器中執行的作業。  
  
-   在 BizTalk Server 管理主控台中的實體連接埠設定  
  
 中的主題將說明這些差異所[移轉 BizTalk 專案建立使用 Siebel 配接器的先前版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。  
  
 不過，您可以使用舊版的配接器所建立的 BizTalk 專案中進行變更並讓它運作以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
 本教學課程提供指示應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。  
  
> [!NOTE]
>  在此教學課程中，為了簡短起見，舊版的 Siebel 配接器將會稱為 vPrev Siebel 配接器。 同樣地，使用 vPrev Siebel 配接器的 BizTalk 專案將被稱為 vPrev BizTalk 專案。  
  
## <a name="sample-used-for-the-tutorial"></a>教學課程使用範例  
 本教學課程根據範例 (Siebel_BussComp_Migration)，示範如何移轉執行插入作業帳戶 Siebel 商務元件上的 vPrev BizTalk 專案。 此範例之提供與 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須 vPrev BizTalk 專案。 本教學課程牽涉到執行插入作業帳戶商務元件上的 BizTalk 專案。  
  
-   您必須擁有執行插入作業使用 vPrev Siebel 配接器帳戶商務元件上的要求訊息。 要求訊息必須符合使用 vPrev Siebel 配接器所產生的插入作業的結構描述。  
  
-   您必須先完成中的步驟[要建立 Siebel 應用程式的必要條件](../../adapters-and-accelerators/adapter-siebel/prerequisites-to-create-siebel-applications.md)。  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案建立使用配接器的先前版本  
 建立 vPrev BizTalk 專案的關鍵要素是：  
  
-   **BizTalk 協調流程**。 這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Siebel Siebel 系統的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。  
  
-   **您想要在 Siebel 商務元件上執行作業的結構描述**。 本教學課程牽涉到執行插入作業帳戶商務元件上的 BizTalk 專案。 帳戶商務元件產生的結構描述是 AccountService_Account_x5d.xsd。 此結構描述會產生使用 vPrev Siebel 配接器。  
  
    > [!NOTE]
    >  不同於 WCF 基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，vPrev Siebel 配接器不支援在商務元件上的特定作業產生的中繼資料。 根據預設，配接器會產生結構描述支援商務元件上的所有作業。 VPrev Siebel 配接器和 WCF 為基礎的多這類差異[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[移轉 BizTalk 專案建立使用 Siebel 配接器的先前版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。  
  
-   **要求訊息**。 要執行插入作業帳戶商務元件上的要求訊息。 因為 vPrev Siebel 配接器所顯示的插入作業結構描述符合要求訊息的結構描述。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>使用舊版的配接器如何移轉 BizTalk 專案建立  
 本移轉教學課程的目標是要讓您傳送要求訊息，符合 vPrev Siebel 配接器使用 WCF 自訂連接埠，可以只處理符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 因此，簡單地說，在移轉作業牽涉到設定不符合以 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]的結構描述。  
  
 不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：  
  
-   產生使用 WCF 為基礎之帳戶商務元件的 Insert 作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
-   執行使用 vPrev Siebel 配接器的要求訊息來執行插入作業使用以 WCF 為基礎的插入作業的要求訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
-   使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]vPrev Siebel 配接器的回應訊息。  
  
-   建立 WCF 自訂 Siebel 傳送接收 BizTalk Server 管理主控台中的連接埠。  
  
-   設定 WCF 自訂連接埠使用的要求和回應的對應。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 修改 vPrev Oracle 資料庫中的 BizTalk 專案](../../adapters-and-accelerators/adapter-oracle-database/step-1-modify-the-vprev-biztalk-project-in-oracle-database.md)  
  
-   [步驟 2： 使用 ORacle 資料庫配接器的 BizTalk Server 管理主控台中設定協調流程](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md)  
  
-   [步驟 3： 測試移轉應用程式使用 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [Siebel 配接器教學課程](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)