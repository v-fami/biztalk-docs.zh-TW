---
title: "第 3 課： 執行預存程序選取 加入新的員工 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec7897e9-0c77-41b2-8cc2-61745bd3b028
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7af49c026b443fb1ca6a0fb7f35b64cdf1e377f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-execute-a-stored-procedure-to-select-new-employees-added"></a>第 3 課： 執行預存程序選取 加入新的員工
了解工作執行在這一課之前，您必須先了解為什麼這些工作所需。 **員工**要新增為新員工插入記錄的資料表中的方式進行定義，**狀態**資料行永遠為"0"每次加入新的員工。 這是好讓您可以使用此資料行查詢新加入的員工，並也會取得通知。 在 SQL Server 中，您會將此查詢執行下列 SQL 陳述式：  
  
```  
SELECT Employee_ID, Name, Designation FROM Employee WHERE Status = 0  
```  
  
 新接收的清單加入員工之後，您也必須更新**狀態**為"1"下, 一次加入新的員工，而且您會執行相同的查詢的資料行，則不會收到記錄的舊的員工。 若要確定上述 Select 陳述式可讓新加入的員工，將會更新**員工**資料表使用下列 SQL 陳述式：  
  
```  
UPDATE Employee SET Status = 1 WHERE Status = 0  
```  
  
 因此，**狀態**舊員工的資料行設定為"1"時新員工一律為"0"。  
  
 在這一課，您將會執行預存程序， **UPDATE_EMPLOYEE**，它接著會執行 Select 和 Update 陳述式。 當您完成本課程之後，您的協調流程會執行下列作業：  
  
1.  收到的任何變更的通知**員工**資料表。  
  
2.  從接收的通知訊息中擷取通知的類型。  
  
3.  如果插入作業的通知訊息，協調流程執行**UPDATE_EMPLOYEE**預存程序。  
  
4.  預存程序讀取新輸入資料錄中的**員工**資料表。 閱讀後新的記錄，預存程序也會設定**狀態**"1"。 這些記錄的資料行  
  
 現在您已經瞭解為何需要執行預存程序。 您現在需要思考如何執行此協調流程的一部分。 協調流程需要的要求訊息**UPDATE_EMPLOYEE**預存程序。 在本教學課程中，您將建立的自訂類別庫會動態建立訊息，然後將它提供給協調流程。 協調流程收到訊息之後，它會將訊息傳送至 SQL Server 使用 SQL 配接器，並接收回應。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)  
  
-   [步驟 2： 將要求訊息傳送至 SQL Server，並接收回應](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)