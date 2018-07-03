---
title: SWIFT 結構描述命名慣例 |Microsoft Docs
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
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dabd9796497bdd5b81d34f71c01124f26de203d9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987423"
---
# <a name="swift-schema-naming-conventions"></a>SWIFT 結構描述命名慣例
Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] Society 結構描述包含使用 BizTalk 編輯器所建立的全球 Interbank 財務電信 (SWIFT) FIN 訊息。 這些結構描述符合整個下列慣例：  
  
> [!NOTE]
>  所有結構描述的版本。 若要查看的版本，開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下方案總管 中的結構描述。 具有\<結構描述\>選取在 「 BizTalk 編輯器 」 中，在 [屬性] 窗格向下捲動到 [標準版本] 屬性中的節點。  
  
- 每個交換的結構描述檔案的名稱是**MT*xxx*.xsd**，其中*xxx* FIN 訊息類型。  
  
- 每個訊息的相關聯的主要原則檔案的名稱是**MT*xxx*_Master_Policy.xml**，而對應的名稱在商務規則引擎 (BRE) 是**MT*xxx*_Master_Policy**，清單名稱取代**MT*xxx*_PolicyList**。  
  
- 每個訊息的相關聯的驗證原則檔的名稱是**MT*xxx*_Validation_Policy.xml**，BRE 中對應的名稱，而且**MT*xxx*_Validation_Policy**。  
  
- 每個訊息結構描述中的根名稱是**SWIFT_CATEGORY*z*_MT*zxx*_Interchange**，其中*z*是訊息類別 （訊息類型的第一個數字） 和*zxx*是訊息類型。  
  
- 每個訊息結構描述的目標命名空間是**<http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx>** <em>，其中 * z</em>是訊息分類 （訊息類型的第一個數字） 及*zxx*是訊息類型。  
  
- 文件類型是**MT * zxx**<em>，其中 * zxx</em>是訊息類型。  
  
- 未編號的欄位和子欄位的名稱包含描述性的商務名稱。 每個單字的第一個字母大寫，而且名稱不包含多餘的空格或標點符號字與字之間 (例如，名稱會是**ServiceIdentifier**，而非**服務識別碼**).  
  
- 在訊息中的序列標籤符合*SWIFT 參考指南*(例如**SequenceA**)。  
  
- 標籤的編號 SWIFT 欄位包含描述性的標題，後面接著序列 （如果有的話），後面接著數字代碼和選擇性的字母格式 (例如**Reference_A_20C**)。  
  
- 當選擇多個欄位的格式時，節點的標籤是 **\<*選擇*\>**，和每個選項則是已編號的欄位 (例如**日期_A_98A**並**DateTime_A_98C**)。  
  
- 最低層級的項目定義的子欄位的名稱是由後面接著子欄位的名稱所組成**型別**(例如**accountType**帳戶)。  
  
  訊息結構描述中的其他命名空間包含下列各項：  
  
- xmlns:xs="<http://www.w3.org/2001/XMLSchema>". 這是預設的 W3C XML 結構描述命名空間。  
  
- xmlns:b ="<http://schemas.microsoft.com/BizTalk/2003>」。 這是預設的 BizTalk 命名空間。  
  
  每個訊息結構描述必須直接參考基底型別和通用結構描述資料型別。  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)