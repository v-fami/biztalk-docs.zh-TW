---
title: 第 3 課： 執行預存程序以選取 加入新員工 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec7897e9-0c77-41b2-8cc2-61745bd3b028
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3021a5e3ead821a0f3c8d0372d48ae469a834c1c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001855"
---
# <a name="lesson-3-execute-a-stored-procedure-to-select-new-employees-added"></a>第 3 課： 執行預存程序來選取新增的員工
在這一課中了解工作執行之前，您必須先了解為何需要這些工作。 **員工**以新增新進員工插入記錄的資料表定義的方式可**狀態**每次將新員工新增 always 資料行設定為"0"。 這麼做是為了讓您可以使用此資料行來查詢新加入的員工，並也收到通知。 在 SQL Server 中，您會將此查詢執行下列 SQL 陳述式：  
  
```  
SELECT Employee_ID, Name, Designation FROM Employee WHERE Status = 0  
```  
  
 新接收的清單加入員工之後，您也必須更新**狀態**為"1"(因此，下一次加入新的員工和您執行相同查詢的資料行，您無法取得記錄的舊的員工。 若要確定上述的 Select 陳述式可讓新加入的員工，您將會更新**員工**資料表使用下列 SQL 陳述式：  
  
```  
UPDATE Employee SET Status = 1 WHERE Status = 0  
```  
  
 因此，**狀態**舊員工的資料行設為"1"的新員工永遠是"0"。  
  
 在這一課，您將執行預存程序中， **UPDATE_EMPLOYEE**，它會依序執行的 Select 和 Update 陳述式。 完成本課程之後，您的協調流程會執行下列作業：  
  
1. 收到的任何變更的通知**員工**資料表。  
  
2. 擷取收到的通知訊息的通知類型。  
  
3. 如果通知訊息是插入作業，協調流程便會執行**UPDATE_EMPLOYEE**預存程序。  
  
4. 預存程序會讀取中的新輸入資料錄**員工**資料表。 閱讀後的新記錄，預存程序也會設定**狀態**"1"。 這些記錄的資料行  
  
   現在您知道您需要執行預存程序。 您現在需要思考如何執行此協調流程的一部分。 協調流程需要的要求訊息**UPDATE_EMPLOYEE**預存程序。 在本教學課程中，您將建立會動態建立訊息並再將它提供給協調流程的自訂類別庫。 協調流程收到訊息之後，它會將訊息傳送至 SQL Server 使用 SQL 配接器，並接收回應。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：為 UPDATE_EMPLOYEE 預存程序建立要求訊息](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)  
  
-   [步驟 2：將要求訊息傳送到 SQL Server 並接收回應](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)