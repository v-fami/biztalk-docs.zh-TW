---
title: 教學課程： 移轉 BizTalk 專案到 Oracle 資料庫配接器 |Microsoft Docs
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
ms.openlocfilehash: cdde0ae8992fc9ae0c7dd30b91b7f38733c1de2b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999839"
---
# <a name="tutorial-migrate-biztalk-projects-to-the-oracle-database-adapter"></a>教學課程： 移轉 BizTalk 專案到 Oracle 資料庫配接器
不同於以 WCF 為基礎的 BizTalk ODBC 配接器，與 Microsoft BizTalk Server 中的出貨針對 Oracle 資料庫[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在許多方面，包括：  
  
- 建立 BizTalk 專案的設計階段經驗。  
  
- 中繼資料的擷取體驗。  
  
- 結構描述檔案名稱和命名空間。  
  
- 資料類型對應。  
  
- 可以使用配接器執行的作業。  
  
- 在 BizTalk Server 管理主控台中的實體連接埠設定  
  
  中的主題會說明這些差異[移轉 BizTalk 專案建立使用 BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。  
  
  不過，您可以對 Oracle 資料庫中使用 BizTalk ODBC 配接器所建立的 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
  本教學課程會提供指示，您應該對現有的 Oracle 資料庫中使用 BizTalk ODBC 配接器所建立的 BizTalk 專案的變更。  
  
> [!NOTE]
>  在本教學課程中，為了保持簡潔，Oracle 資料庫的 BizTalk ODBC 配接器會稱為 「 vPrev Oracle 資料庫配接器 」。 同樣地，使用 vPrev Oracle 資料庫配接器的 BizTalk 專案會被稱為 「 vPrev BizTalk 專案 」。  
  
## <a name="sample-used-for-the-tutorial"></a>用於本教學課程的範例  
 本教學課程是以示範如何移轉 vPrev BizTalk 專案的範例 (Oracle_Migration) 為基礎。 提供了 Microsoft 範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
- 您必須具有 vPrev BizTalk 專案。 本教學課程包含執行插入作業的客戶資料表上的 BizTalk 專案。 CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。  
  
- 您必須擁有執行插入作業使用 vPrev Oracle 資料庫配接器的 Oracle 資料庫上的要求訊息。 使用 vPrev Oracle 資料庫配接器所產生的插入作業的結構描述必須符合 「 要求 」 訊息。  
  
- 您必須先完成中的步驟[必要條件](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md) 
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案使用舊版配接器的建立  
 建立 vPrev BizTalk 專案的關鍵要素是：  
  
- **BizTalk 協調流程**。 這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 Oracle 的 Oracle 資料庫的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。  
  
- **您想要的 Oracle 資料庫上執行的作業結構描述**。 本教學課程包含 SCOTT 結構描述中，執行插入作業在 CUSTOMER 資料表上的 BizTalk 專案。 CUSTOMER 資料表由 SCOTT 結構描述下執行 SQL 指令碼隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。 產生針對 CUSTOMER 資料表的結構描述是 CUSTOMERService_CUSTOMER_x5d.xsd。 此結構描述是使用 vPrev Oracle 資料庫配接器所產生的。  
  
  > [!NOTE]
  >  不同於以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，vPrev Oracle 資料庫配接器不支援在 Oracle 資料庫資料表上的特定作業產生的中繼資料。 根據預設，配接器會產生結構描述支援的資料表的所有作業。 多個這類之間的差異 vPrev Oracle 資料庫配接器以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 移轉 BizTalk 專案建立使用 BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e)。  
  
- **要求訊息**。 要執行插入作業在 CUSTOMER 資料表上的要求訊息。 如先前版本的 Oracle 資料庫配接器所呈現的插入作業結構描述符合要求訊息的結構描述。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>如何移轉 BizTalk 專案可讓您建立使用舊版的配接器  
 本移轉教學課程的目標是要讓您傳送要求訊息，產生 vPrev Oracle 資料庫配接器，使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息結構描述符合[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的結構描述。  
  
 不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：  
  
- 產生 SCOTT 的 Insert 作業的中繼資料。使用以 WCF 為基礎的 CUSTOMER 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
- 執行插入作業使用 vPrev Oracle 資料庫配接器的要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
- 將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]vPrev Oracle 資料庫配接器的回應訊息。  
  
- 建立 WCF 自訂 Oracle 傳送接收 BizTalk Server 管理主控台中的連接埠。  
  
- 設定 WCF 自訂連接埠，若要使用的要求和回應的對應。  
  
 
  
## <a name="see-also"></a>另請參閱  
[開始使用 Biztalk Server](../../core/getting-started-with-biztalk-server.md)