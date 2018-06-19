---
title: 教學課程： 將 BizTalk 專案移轉至 Oracle 資料庫配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a393219-bae8-4e08-acc8-76986600d0de
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0948e79b7f236bb20bbff9101195809bcc921a68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215342"
---
# <a name="tutorial-migrate-biztalk-projects-to-the-oracle-database-adapter"></a>教學課程： 將 BizTalk 專案移轉至 Oracle 資料庫配接器
BizTalk ODBC 配接器，為 Microsoft BizTalk server 隨附 Oracle 資料庫與 WCF 架構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在許多方面，包括：  
  
-   建立 BizTalk 專案的設計階段經驗。  
  
-   中繼資料擷取的經驗。  
  
-   結構描述檔案名稱和命名空間。  
  
-   資料類型對應。  
  
-   可以使用配接器中執行的作業。  
  
-   在 BizTalk Server 管理主控台中的實體連接埠設定  
  
 中的主題將說明這些差異所[移轉 BizTalk 專案建立使用 Oracle 資料庫的 BizTalk ODBC 配接器](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。  
  
 不過，您可以變更使用 Oracle 資料庫的 BizTalk ODBC 配接器所建立的 BizTalk 專案，並讓它運作以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 本教學課程提供的變更，您應該對現有的 BizTalk 專案建立 BizTalk ODBC 配接器使用 Oracle 資料庫的指示。  
  
> [!NOTE]
>  在此教學課程中，為了簡短起見，BizTalk ODBC Adapter for Oracle 資料庫將被稱為 「 vPrev Oracle 資料庫介面卡 」。 同樣地，使用 vPrev Oracle 資料庫配接器的 BizTalk 專案將被稱為 「 vPrev BizTalk 專案 」。  
  
## <a name="sample-used-for-the-tutorial"></a>教學課程使用範例  
 本教學課程根據範例 (Oracle_Migration)，示範如何移轉 vPrev BizTalk 專案。 此範例之提供與 Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須 vPrev BizTalk 專案。 本教學課程牽涉到執行插入作業的客戶資料表上的 BizTalk 專案。 CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。  
  
-   您必須擁有執行插入作業使用 vPrev Oracle 資料庫配接器的 Oracle 資料庫上的要求訊息。 要求訊息必須符合使用 vPrev Oracle 資料庫配接器所產生的插入作業的結構描述。  
  
-   您必須先完成中的步驟[必要條件](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md) 
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案建立使用配接器的先前版本  
 建立 vPrev BizTalk 專案的關鍵要素是：  
  
-   **BizTalk 協調流程**。 這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Oracle 與 Oracle 資料庫的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。  
  
-   **您想要在 Oracle 資料庫上執行作業的結構描述**。 本教學課程牽涉到客戶資料表上的 Insert 作業執行 SCOTT 結構描述中的 BizTalk 專案。 CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。 產生客戶資料表的結構描述是 CUSTOMERService_CUSTOMER_x5d.xsd。 此結構描述會產生使用 vPrev Oracle 資料庫配接器。  
  
    > [!NOTE]
    >  不同於 WCF 基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，vPrev Oracle 資料庫配接器不支援針對 Oracle 資料庫資料表上的特定作業產生的中繼資料。 根據預設，配接器會產生結構描述支援的資料表的所有作業。 VPrev Oracle 資料庫配接器和 WCF 為基礎的多這類差異[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[移轉 BizTalk 專案建立使用 Oracle 資料庫的 BizTalk ODBC 配接器](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。  
  
-   **要求訊息**。 要執行插入作業客戶資料表上的要求訊息。 因為由舊版的 Oracle 資料庫配接器顯示的插入作業結構描述符合要求訊息的結構描述。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>使用舊版的配接器如何移轉 BizTalk 專案建立  
 本移轉教學課程的目標是要讓您傳送要求訊息，符合 vPrev Oracle 資料庫配接器，使用 WCF 自訂連接埠，可以只處理符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 因此，簡單地說，在移轉作業牽涉到設定不符合以 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的結構描述。  
  
 不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：  
  
-   產生 SCOTT 的 Insert 作業的中繼資料。使用 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
-   執行使用 vPrev Oracle 資料庫配接器的要求訊息來執行插入作業使用以 WCF 為基礎的插入作業的要求訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
-   使用 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]vPrev Oracle 資料庫配接器的回應訊息。  
  
-   建立 WCF 自訂 Oracle 傳送接收 BizTalk Server 管理主控台中的連接埠。  
  
-   設定 WCF 自訂連接埠使用的要求和回應的對應。  
  
 
  
## <a name="see-also"></a>另請參閱  
[Biztalk Server 使用者入門](../../core/getting-started-with-biztalk-server.md)