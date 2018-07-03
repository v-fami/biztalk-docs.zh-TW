---
title: 教學課程 2： 員工-訂單程序使用 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eeb4dd1e-209a-47eb-9c0e-a138e02f0ff2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d14008611bfb22bf39e446e72ecb3bba4571761
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010775"
---
# <a name="tutorial-2-employee---purchase-order-process-using-the-sql-adapter"></a>教學課程 2： 員工-訂單程序使用 SQL 配接器
在本教學課程中，您就會自動將設備的採購部門位置順序每次新的員工加入組織的程序。 員工詳細資料和採購單詳細資料保存在**員工**並**為 Purchase_Order**資料表分別在 SQL Server 資料庫。 採購部門獲知更新為 Purchase_Order 資料表中的 SQL Server 資料庫，以及傳送電子郵件。 在處理序中，執行下列動作：  
  
1. 配接器接收的通知每次**員工**會更新資料表。 然後，配接器會傳送通知給 BizTalk 協調流程。  
  
2. BizTalk 協調流程會找出通知是否為新記錄插入至**員工**資料表。 如果通知是任何其他作業上**員工**資料表中，協調流程不會執行任何作業。  
  
3. 如果通知是在插入作業**員工**通知，已加入新的員工資料錄，協調流程使用的資料表[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]讀取新的記錄詳細資料。  
  
4. 協調流程收到回應，其中包含新加入的員工記錄的詳細資料。 協調流程對應**Employee_ID**並**指定**欄位以回應插入作業的要求訊息上**為 Purchase_Order**資料表。  
  
5. 協調流程接著會使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]上執行插入作業**為 Purchase_Order**資料表。 插入作業的回應會傳送至採購部門中，以電子郵件。  
  
## <a name="about-the-database-objects-used-in-this-sample"></a>此範例中使用的資料庫物件的相關  
 本教學課程會使用隨附於範例 SQL 指令碼所建立的資料庫物件。 如需有關此指令碼和範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。 您將在本教學課程中使用的資料庫物件如下：  
  
- **ADAPTER_SAMPLES**資料庫。  
  
- **員工**並**為 Purchase_Order**資料表。  
  
- **UPDATE_EMPLOYEE**預存程序。  
  
  當您執行範例所提供的 SQL 指令碼時，會建立所有這些資料庫物件。 請確定在開始本教學課程之前，執行指令碼。  
  
## <a name="sample-based-on-this-tutorial"></a>根據此教學課程的範例  
 範例中， **Employee_PurchaseOrder**，根據本教學課程也會提供與[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
 我們建議您瀏覽本教學課程完全了解如何建立使用配接器的 BizTalk 專案，並再看看此範例做為參考。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [第 1 課：產生結構描述和建立訊息](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)  
  
-   [第 2 課：接收和篩選通知](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)  
  
-   [第 3 課：執行預存程序以選取新增的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)  
  
-   [第 4 課：在訂單資料表上執行插入作業](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)  
  
-   [第 5 課：部署方案](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)