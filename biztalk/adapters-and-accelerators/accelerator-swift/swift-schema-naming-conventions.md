---
title: SWIFT 命名慣例的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- naming conventions [schemas]
- schemas, naming conventions
ms.assetid: 3c1f2519-2575-4178-89c1-e97333c1e6bd
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14245a185adcccdfb1f2ea2ed9382820fb84177e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="swift-schema-naming-conventions"></a>SWIFT 的結構描述的命名慣例
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] 使用 BizTalk 編輯器所建立的全球 Interbank 財務 Telecommunication (SWIFT) FIN 訊息協會包含結構描述。 這些結構描述符合整個下列慣例：  
  
> [!NOTE]
>  所有結構描述具有版本設定。 若要查看版本，開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下方案總管 中的結構描述。 與\<結構描述\>在 BizTalk 編輯器中，選取屬性 窗格向下捲動到 標準版本 屬性中的節點。  
  
-   每個交換的結構描述檔案的名稱是**MT*xxx*.xsd**，其中*xxx*是 FIN 訊息類型。  
  
-   每個訊息的相關聯的主要原則檔案的名稱是**MT*xxx*_Master_Policy.xml**，且對應的名稱在商務規則引擎 (BRE) 是**MT*xxx*_Master_Policy**，清單名稱為**MT*xxx*_PolicyList**。  
  
-   每個訊息相關聯的驗證原則檔案的名稱是**MT*xxx*_Validation_Policy.xml**，BRE 中對應的名稱，且**MT*xxx*_Validation_Policy**。  
  
-   在每個訊息結構描述中，根目錄的名稱是**SWIFT_CATEGORY*z*_MT*zxx*_Interchange**，其中*z*是訊息類別 （訊息類型的第一個數字） 和*zxx*是訊息類型。  
  
-   每個訊息結構描述的目標命名空間是 **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx * * *，其中*z*是訊息類別 （訊息類型的第一個數字） 和*zxx*是訊息類型。  
  
-   文件類型為 **MT*zxx * * *，其中*zxx*是訊息類型。  
  
-   不會編號的欄位與欄位名稱的子包含描述性的商務名稱。 每個單字的第一個字母大寫，它的名稱不包含空格或標點符號字與字之間 (例如，名稱會是**ServiceIdentifier**，而非**Service 識別碼**).  
  
-   在訊息中的時序的標籤符合*SWIFT 參考指南*(例如， **SequenceA**)。  
  
-   標籤的編號 SWIFT 欄位包含一個描述性標題，後面接著序列 （如果有的話），後面接著數字代碼和選擇性的字母格式 (例如， **Reference_A_20C**)。  
  
-   有多種格式欄位的選擇，節點的標籤時是 **\<*選擇*\>**，和每個選項則是已編號的欄位 (例如，**日期_A_98A**和**DateTime_A_98C**)。  
  
-   最低層級項目定義的子欄位的名稱所組成的名稱後面的子欄位**類型**(例如， **accountType**帳戶)。  
  
 其他命名空間中的訊息結構描述包括：  
  
-   xmlns:xs="http://www.w3.org/2001/XMLSchema". 這是預設的 W3C XML 結構描述命名空間。  
  
-   xmlns:b="http://schemas.microsoft.com/BizTalk/2003". 這是預設的 BizTalk 命名空間。  
  
 每個訊息結構描述直接參考基底類型和常見的資料類型結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)