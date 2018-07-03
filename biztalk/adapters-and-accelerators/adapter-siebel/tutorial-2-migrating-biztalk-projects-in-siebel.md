---
title: 教學課程 2： Siebel 中的移轉 BizTalk 專案 |Microsoft Docs
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
ms.openlocfilehash: 3ada19454c3d2aef1c725987d8d37f7b98a2d1c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996431"
---
# <a name="tutorial-2-migrating-biztalk-projects-in-siebel"></a>教學課程 2： 移轉 BizTalk 專案中 Siebel
Siebel 配接器隨附於 Microsoft BizTalk Server 的先前版本不同於以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在許多方面，包括：  
  
- 建立 BizTalk 專案的設計階段經驗。  
  
- 中繼資料的擷取體驗。  
  
- 結構描述檔案名稱和命名空間。  
  
- 資料類型對應。  
  
- 可以使用配接器執行的作業。  
  
- 在 BizTalk Server 管理主控台中的實體連接埠設定  
  
  中的主題會說明這些差異[移轉 BizTalk 專案建立使用 Siebel 配接器的上一個版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。  
  
  不過，您可以對使用舊版的配接器建立 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
  本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。  
  
> [!NOTE]
>  在本教學課程中，為了保持簡潔，舊版的 Siebel 配接器會稱為 vPrev Siebel 配接器。 同樣地，使用 vPrev Siebel 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。  
  
## <a name="sample-used-for-the-tutorial"></a>用於本教學課程的範例  
 本教學課程是以示範如何移轉 vPrev BizTalk 專案，執行插入作業帳戶 Siebel 商務元件上的範例 (Siebel_BussComp_Migration) 為基礎。 提供了 Microsoft 範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須具有 vPrev BizTalk 專案。 本教學課程包含執行插入作業帳戶商務元件上的 BizTalk 專案。  
  
-   您必須擁有執行插入作業帳戶商務元件使用 vPrev Siebel 配接器上的要求訊息。 使用 vPrev Siebel 配接器所產生的插入作業的結構描述必須符合 「 要求 」 訊息。  
  
-   您必須先完成中的步驟[要建立 Siebel 應用程式的必要條件](../../adapters-and-accelerators/adapter-siebel/prerequisites-to-create-siebel-applications.md)。  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案使用舊版配接器的建立  
 建立 vPrev BizTalk 專案的關鍵要素是：  
  
- **BizTalk 協調流程**。 這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Siebel Siebel 系統的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。  
  
- **您想要在 Siebel 商務元件上執行的作業結構描述**。 本教學課程包含執行插入作業帳戶商務元件上的 BizTalk 專案。 帳戶商務元件所產生的結構描述是 AccountService_Account_x5d.xsd。 此結構描述是使用 vPrev Siebel 配接器所產生的。  
  
  > [!NOTE]
  >  不同於以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，vPrev Siebel 配接器不支援在商務元件上的特定作業產生的中繼資料。 根據預設，配接器會產生結構描述支援商務元件上的所有作業。 多個這類之間的差異 vPrev Siebel 配接器以 WCF 為基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 <<c2> [ 移轉 BizTalk 專案建立使用 Siebel 配接器的上一個版本](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e)。  
  
- **要求訊息**。 要執行 Insert 作業帳戶商務元件上的要求訊息。 因為呈現 vPrev Siebel 配接器的插入作業結構描述符合要求訊息的結構描述。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>如何移轉 BizTalk 專案可讓您建立使用舊版的配接器  
 本移轉教學課程的目標是要讓您傳送要求訊息，這符合 vPrev Siebel 配接器使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]的結構描述。  
  
 不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：  
  
- 產生使用 WCF 為基礎的商務帳戶元件上的插入作業的中繼資料[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
- 執行插入作業使用 vPrev Siebel 配接器要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
- 將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]vPrev Siebel 配接器的回應訊息。  
  
- 建立 WCF 自訂 Siebel 傳送接收 BizTalk Server 管理主控台中的連接埠。  
  
- 設定 WCF 自訂連接埠，若要使用的要求和回應的對應。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 修改 vPrev BizTalk 專案中 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/step-1-modify-the-vprev-biztalk-project-in-oracle-database.md)  
  
-   [步驟 2： 設定協調流程中使用 ORacle 資料庫配接器的 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md)  
  
-   [步驟 3： 測試移轉應用程式與 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [Siebel 配接器教學課程](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)