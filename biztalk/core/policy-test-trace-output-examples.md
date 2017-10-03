---
title: "原則測試追蹤輸出範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, policies
- policies, testing
- testing, examples
ms.assetid: 92e1dc7f-1a8d-41a5-84b6-46d5ad9f2ef2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3678769dffa03bb77c3e86fef02998a354b1fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="policy-test-trace-output-examples"></a>原則測試追蹤輸出範例
本章節包含不同事實類型的原則測試輸出範例。  
  
## <a name="net-class"></a>.Net 類別  
 原則 "LoanProcessing" 中的範例規則 "TestRule1"：  
  
```  
IF test.get_ID > 0  
THEN <do something>  
```  
  
 **輸出：**  
  
 規則集的規則引擎追蹤： LoanProcessing 3/16/2004年上午 9:50:28  
  
 事實活動 3/16/2004年上午 9:50:28  
  
 規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型：MyTest.test  
  
 物件執行個體識別碼： 872  
  
 條件評估測試 （符合） 3/16/2004年上午 9:50:28  
  
 規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 規則集名稱：LoanProcessing  
  
 測試運算式： MyTest.test.get_ID > 0  
  
 左運算元值： 100  
  
 右運算元值： 0  
  
 測試結果：True  
  
 議程更新 3/16/2004年上午 9:50:28  
  
 規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/16/2004年上午 9:50:28  
  
 規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 3/16/2004年上午 9:50:28  
  
 規則引擎執行個體識別項：9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型：MyTest.test  
  
 物件執行個體識別碼： 872  
  
## <a name="dataconnectiontypeddatarow"></a>DataConnection/TypedDataRow  
 原則 "LoanProcessing" 中的範例規則 "TestRule1"：  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 **輸出：**  
  
 規則集的規則引擎追蹤： LoanProcessing 3/16/2004年 8:30:16 AM  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： DataConnection:Northwind:CustInfo  
  
 物件執行個體識別碼： 874  
  
 條件評估測試 （符合） 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 測試運算式： 選取 * 從 [CustInfo]，[CreditCardBalance] > 0  
  
 左運算元值：  
  
 右運算元值：  
  
 測試結果：True  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 177556  
  
 議程更新 3/16/2004 08:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 177559  
  
 議程更新 3/16/2004 08:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 177558  
  
 議程更新 3/16/2004 08:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/16/2004 08:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/16/2004 08:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/16/2004 08:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： DataConnection:Northwind:CustInfo  
  
 物件執行個體識別碼： 874  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 177559  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 177558  
  
 事實活動 3/16/2004年 8:30:16 AM  
  
 規則引擎執行個體識別碼： 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 177556  
  
 上述範例指出 CustInfo 表格中有三列符合規則中的條件。  這導致三個唯一的 TypedDataRows 判斷提示至引擎，並造成每個執行個體發生議程更新和規則引發。  
  
## <a name="typedatatabletypeddatarow"></a>TypeDataTable/TypedDataRow  
 原則 "LoanProcessing" 中的範例規則 "TestRule1"：  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 **輸出：**  
  
 規則集的規則引擎追蹤： LoanProcessing 3/17/2004年 11:27:35 AM  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedDataTable:Northwind:CustInfo  
  
 物件執行個體識別碼： 377  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 376  
  
 條件評估測試 (符合) 3/17/2004 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 測試運算式： TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 左運算元值： 500  
  
 右運算元值： 0  
  
 測試結果：True  
  
 議程更新 3/17/2004年 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 375  
  
 條件評估測試 (符合) 3/17/2004 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 測試運算式： TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 左運算元值： 1000年  
  
 右運算元值： 0  
  
 測試結果：True  
  
 議程更新 3/17/2004年 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 374  
  
 條件評估測試 (符合) 3/17/2004 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 測試運算式： TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 左運算元值： 35000  
  
 右運算元值： 0  
  
 測試結果：True  
  
 議程更新 3/17/2004年 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/17/2004年 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/17/2004年 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/17/2004年 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedDataTable:Northwind:CustInfo  
  
 物件執行個體識別碼： 377  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 375  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 374  
  
 事實活動 17.03.04 11:27:35 AM  
  
 規則引擎執行個體識別碼： 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedDataRow:Northwind:CustInfo  
  
 物件執行個體識別碼： 376  
  
> [!NOTE]
>  上述範例顯示 TypedDataTable 包含三個資料列，且會將每一個資料列判斷提示為 TypedDataRow。  每個資料列在條件中都會評估為 True，且會造成規則新增至議程並引發規則。  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 原則 "LoanProcessing" 中的範例規則 "TestRule1"：  
  
```  
IF Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4  
THEN <do something>  
```  
  
 **輸出：**  
  
 規則集的規則引擎追蹤： LoanProcessing 2004 年 3 月 17 日上午 9:23:05  
  
 事實活動 2004 年 3 月 17 日上午 9:23:05  
  
 規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case  
  
 物件執行個體識別碼： 858  
  
 事實活動 2004 年 3 月 17 日上午 9:23:05  
  
 規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 規則集名稱：LoanProcessing  
  
 作業：判斷提示  
  
 物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType  
  
 物件執行個體識別碼： 853  
  
 條件評估測試 （符合） 3/17/2004年上午 9:23:05  
  
 規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 規則集名稱：LoanProcessing  
  
 測試運算式： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths > = 4  
  
 左運算元值： 6  
  
 右運算元值： 4  
  
 測試結果：True  
  
 議程更新 3/17/2004年上午 9:23:05  
  
 規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 規則集名稱：LoanProcessing  
  
 作業：新增  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 規則被引發 3/17/2004年上午 9:23:05  
  
 規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 規則集名稱：LoanProcessing  
  
 規則名稱： TestRule1  
  
 衝突解決準則： 0  
  
 事實活動 2004 年 3 月 17 日上午 9:23:05  
  
 規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case  
  
 物件執行個體識別碼： 858  
  
 事實活動 2004 年 3 月 17 日上午 9:23:05  
  
 規則引擎執行個體識別碼： 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 規則集名稱：LoanProcessing  
  
 作業： 撤銷  
  
 物件類型： TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType  
  
 物件執行個體識別碼： 853  
  
 這個範例將示範**TypedXmlDocument**已判斷提示至引擎，以"microsoft.samples.biztalk.loansprocessor.case"的文件類型。  根據規則中定義的 XPath 選取器，引擎接著會依據文件類型與選取器字串，以 "Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType" 類型來建立和判斷提示子 TypedXmlDocument。  
  
 此子 TypedXmlDocument 在條件中評估為 True，造成議程更新和規則引發。  父和子**TypedXmlDocument**的然後撤回。  
  
## <a name="update-function"></a>更新功能  
 範例原則 "Order"  
  
 **"InventoryCheck"規則**  
  
```  
IF Inventory.AllocateInventory == True  
THEN Order.inventoryAvailable == True  
   Update(Order)  
```  
  
 **"Ship"規則**  
  
```  
IF Order.inventoryAvailable == True  
THEN Shipment.ShipOrder  
```  
  
 **輸出：**  
  
 規則集的規則引擎追蹤： 排序 2004 年 3 月 17 日上午 10:31:17  
  
 事實活動 2004 年 3 月 17 日上午 10:31:17  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業：判斷提示  
  
 物件類型： TestClasses.Order  
  
 物件執行個體識別碼： 448  
  
 條件評估測試 （符合） 3/17/2004年 10:31:17 AM  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 測試運算式： TestClasses.Order.inventoryAvailable = = True  
  
 左運算元值： null  
  
 右運算元值： True  
  
 測試結果： False  
  
 事實活動 2004 年 3 月 17 日上午 10:31:17  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業：判斷提示  
  
 物件類型： TestClasses.Shipment  
  
 物件執行個體識別碼： 447  
  
 事實活動 2004 年 3 月 17 日上午 10:31:17  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業：判斷提示  
  
 物件類型： TestClasses.Inventory  
  
 物件執行個體識別碼： 446  
  
 條件評估測試 （符合） 3/17/2004年 10:31:17 AM  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 測試運算式： TestClasses.Inventory.AllocateInventory = = True  
  
 左運算元值： True  
  
 右運算元值： True  
  
 測試結果：True  
  
 議程更新 3/17/2004年 10:31:17 AM  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業：新增  
  
 規則名稱： InventoryCheck  
  
 衝突解決準則： 0  
  
 規則被引發 3/17/2004年 10:31:17 AM  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 規則名稱： InventoryCheck  
  
 衝突解決準則： 0  
  
 事實活動 2004 年 3 月 17 日上午 10:31:17  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業： 更新  
  
 物件類型： TestClasses.Order  
  
 物件執行個體識別碼： 448  
  
 條件評估測試 （符合） 3/17/2004年 10:31:17 AM  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 測試運算式： TestClasses.Order.inventoryAvailable = = True  
  
 左運算元值： True  
  
 右運算元值： True  
  
 測試結果：True  
  
 議程更新 3/17/2004年 10:31:17 AM  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業：新增  
  
 規則名稱： 出貨  
  
 衝突解決準則： 0  
  
 規則被引發 3/17/2004年 10:31:17 AM  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 規則名稱： 出貨  
  
 衝突解決準則： 0  
  
 事實活動 2004 年 3 月 17 日上午 10:31:17  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業： 撤銷  
  
 物件類型： TestClasses.Order  
  
 物件執行個體識別碼： 448  
  
 事實活動 2004 年 3 月 17 日上午 10:31:17  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業： 撤銷  
  
 物件類型： TestClasses.Shipment  
  
 物件執行個體識別碼： 447  
  
 事實活動 2004 年 3 月 17 日上午 10:31:17  
  
 規則引擎執行個體識別碼： 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 規則集名稱： 順序  
  
 作業： 撤銷  
  
 物件類型： TestClasses.Inventory  
  
 物件執行個體識別碼： 446  
  
 在此範例中，在第一次檢查與 Ship 規則相關聯的條件時，它會評估為 False。  但是，當 InventoryCheck 規則引發時，Order 的 inventoryAvailable 欄位會變更，且在引擎上發出對 Order 物件更新命令。  這會造成重新評估 Ship 規則。  這一次，此條件會評估為 True，並引發 Ship 規則。  
  
> [!NOTE]
>  如果您的規則撰寫不正確，使用更新功能正向鏈結可能會導致無限迴圈。  若發生此情況，您會在商務規則編輯器中測試原則時，收到文字為「規則引擎偵測到執行迴圈」的錯誤訊息。