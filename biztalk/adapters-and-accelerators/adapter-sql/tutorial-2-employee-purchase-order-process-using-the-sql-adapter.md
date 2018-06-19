---
title: 教學課程 2： 員工-訂單程序使用 SQL 配接器 |Microsoft 文件
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
ms.openlocfilehash: 8fca0c11aeb1f84a5e9f05a4df4f995b7c2b52e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223230"
---
# <a name="tutorial-2-employee---purchase-order-process-using-the-sql-adapter"></a>教學課程 2： 員工-訂單程序使用 SQL 配接器
在本教學課程中，您要將自動化位置放置設備的採購部門順序每次新的員工聯結組織的程序。 員工詳細資料及訂單詳細資料會保留在**員工**和**Purchase_Order**資料表分別將 SQL Server 資料庫中。 採購部門會在透過更新 Purchase_Order 資料表中的 SQL Server 資料庫及傳送電子郵件通知。 在此程序，會發生下列動作：  
  
1.  配接器接收的通知每次**員工**資料表更新。 配接器便會將通知傳送給 BizTalk 協調流程。  
  
2.  BizTalk 協調流程找出通知是否為新記錄插入至**員工**資料表。 如果通知的任何其他作業，則在**員工**資料表中，協調流程不會執行任何作業。  
  
3.  如果在通知，則插入作業**員工**通知，已加入新的員工記錄，協調流程使用的資料表[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]讀取新記錄的詳細資訊。  
  
4.  協調流程收到回應，其中包含新加入的員工記錄的詳細資訊。 協調流程對應**Employee_ID**和**指定**插入作業的要求訊息的回應中的欄位上**Purchase_Order**資料表。  
  
5.  協調流程接著會使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]上執行插入作業**Purchase_Order**資料表。 插入作業的回應為當做電子郵件傳送給採購部門。  
  
## <a name="about-the-database-objects-used-in-this-sample"></a>此範例中使用的資料庫物件的相關  
 本教學課程會使用隨附於範例 SQL 指令碼所建立的資料庫物件。 如需指令碼和範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。 您將在本教學課程使用的資料庫物件如下：  
  
-   **ADAPTER_SAMPLES**資料庫。  
  
-   **員工**和**Purchase_Order**資料表。  
  
-   **UPDATE_EMPLOYEE**預存程序。  
  
 當您執行範例隨附的 SQL 指令碼時，會建立所有這些資料庫物件。 請確定在開始此教學課程之前，執行指令碼。  
  
## <a name="sample-based-on-this-tutorial"></a>根據此教學課程的範例  
 範例中， **Employee_PurchaseOrder**，這根據此教學課程也會提供與[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
 我們建議您進行教學課程，完全以了解如何建立使用配接器的 BizTalk 專案，然後查看範例做為參考。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [第 1 課： 產生結構描述和建立訊息](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)  
  
-   [第 2 課： 接收和篩選器通知](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)  
  
-   [第 3 課： 執行預存程序選取 加入新的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)  
  
-   [第 4 課： 執行插入作業的採購訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)  
  
-   [第 5 課： 部署方案](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)