---
title: 使用不可部分完成交易的案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], examples
- Scope shape [Orchestration Designer], atomic transactions
- transactions, examples
- transactions, atomic
- atomic transactions, examples
- examples, atomic transactions
ms.assetid: f3481b4e-7e7e-47f0-b8f4-6012a2fc5310
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e73cfea7a99e2fafbf115a367dbf0840de3369c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270942"
---
# <a name="scenarios-using-atomic-transactions"></a>使用不可部分完成交易的案例
下列案例將描述不可部分完成交易的用法。  
  
## <a name="scenario-1-an-atomic-transaction-with-com-servicedcomponent"></a>案例 1: 不可部分完成交易具有 COM + ServicedComponent  
 下列的協調流程示範如何使用**RetryTransactionException**不可部分完成交易。 雖然在不可部分完成的範圍中無法直接包含例外狀況處理常式，但該範圍可以包含非交易式的範圍，非交易式的範圍中就可以具備例外狀況處理常式。 **ServicedComponent**在相同的 DTC 交易中登記和元件所引發的例外狀況會遭到攔截並重新擲回為**RetryTransactionException**。 (這是假設**重試**屬性設定為**True**不可部分完成的範圍)。  
  
 請注意，擱置協調流程會而 MessageAssignment 圖形中的動作會回復即使**RetryTransactionException**不會擲回。 不過，這種模式可以使自動產生重試作業的應用程式更有恢復力。  
  
 **具有 COM + ServicedComponent 的不可部分完成交易**  
  
 ![與 COM &#43; 不可部分完成交易ServicedComponent](../core/media/bts-trans-orch-fig5.gif "BTS_Trans_Orch_Fig5")  
  
## <a name="scenario-2-using-transacted-adapters-with-atomic-transactions"></a>案例 2： 將交易配接器使用不可部分完成交易  
 下列的協調流程顯示如何以 SQL 配接器使用不可部分完成的交易。 整個協調流程標示為長時間執行個別的不可部分完成交易的兩個邏輯部分的工作： 客戶 插入新的 「 客戶 」 和 「 插入訂單詳細資料。  
  
 如果訂單插入工作因為任何原因而失敗，則客戶插入工作將會回復。 此範例使用 SQL 配接器來執行資料庫作業。 如前所述，與不可部分完成之交易相關的範圍，會在訊息傳送至 MessageBox 資料庫時完成。 這代表當引擎成功傳送 Scope_InsertCustomer 和 Scope_InsertOrder 範圍中的訊息之後，各範圍就會認可。 SQL 配接器會針對客戶或訂單的實際插入工作建立新的交易。  
  
 連接埠擁有 Delivery Notification 屬性，可驗證訊息已透過傳送埠而成功傳送。 當 Delivery Notification 屬性設定為 "Transmitted" 時，會在傳送作業的交易認可點之前放置接收訂閱。 不過，以不可部分完成的範圍來說，接收訂閱會放在包含此範圍的父範圍中。  
  
 在 InsertOrder SQL 交易失敗的案例中，會傳回 "Nack" 並認可 "Scope_InsertOrder"。 在傳送埠耗盡設定的重試次數後，就會引發 DeliveryFailureException。 此例外狀況會由預設的例外狀況處理常式所攔截 (該處理常式將執行預設的補償程序)。 如此將引發與 Scope_InsertCustomer 和 Scope_InsertOrder 相關聯的補償處理常式，導致客戶資訊插入作業復原。  
  
> [!NOTE]
>  將這兩個範圍巢狀化於長時間執行的範圍中，以及從例外狀況處理常式叫用長時間執行範圍的補償圖形 (目標為長時間執行的交易)，會導致與上述相同的行為。 您不能將整個協調流程標示為不可部分完成，因為不可部分完成的交易不允許巢狀化交易。  
  
 **不可部分完成交易的交易配接器**  
  
 ![交易式配接器使用不可部分完成交易](../core/media/bts-trans-orch-fig6.gif "BTS_Trans_Orch_Fig6")