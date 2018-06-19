---
title: 使用結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing, schemas
- schemas, developing
ms.assetid: 123c4b43-34e4-41c7-980d-5d518b1479c1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 404beaeb617f7a6c0c5e3fc4ddc40126e6b97990
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963092"
---
# <a name="working-with-schemas"></a>使用結構描述
中提供的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]是[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]協會全球 Interbank 財務 Telecommunication (SWIFT) FIN 訊息的 XSD 表示法。 每個訊息類型都有自己的結構描述，包括 SWIFT 標頭和 SWIFT trailer （交換格式）。 此結構描述便可傳送或接收 SWIFT 的訊息。 這些結構描述是唯一的分隔和位置記錄，以提供詳細的 XML 表示法，一般檔案 FIN 結構的混合。  
  
 大部分的 SWIFT 客戶使用 SWIFT FIN 訊息相對較小的子集。 若要實作解決方案，這些客戶，您可以建立 BizTalk 結構描述專案 (如所示[單元 2： 加入新的結構描述專案](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md)A4SWIFT 教學課程的)。 新增相關的訊息結構描述 (MT*xxx*.xsd) 從\\\ Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category x\MT xyy 目錄，其中 x 是 FIN 訊息類型的第一個數字，而 xyy 是訊息的三位數的訊息類型。  
  
 您可以將數個結構描述加入至相同的專案。 若要維護可管理性，您不應該新增 20 個以上的訊息結構描述，每個專案。 您也需要將基底且常見的結構描述加入至專案。 如果您已部署的基底且常見的結構描述，您需要在它們的組件參考，而不是將其部署。 本章節描述這些結構描述。 訊息結構描述就可以開始使用，因為是 SWIFT 網路傳送的訊息和接收來自 SWIFT 的訊息。  
  
 您可以檢查每個 SWIFT 的結構描述中的內容[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]使用結構描述編輯器。 所有訊息交換的結構描述有下列的一般結構：  
  
-   標頭  
  
-   訊息文字  
  
-   結尾  
  
 本章節描述的標頭和結尾結構描述。 訊息文字包含 FIN 訊息的裝載和包含的所有資料欄位包含寄件者、 接收者和訊息類型的欄位除外。 這三個欄位都包含在標頭部分。 有些訊息也包含選擇性的使用者標頭，也會提供處理資訊。  
  
 每個 FIN 訊息內容是由一系列的定義順序中的欄位所組成。 這些欄位符合下列規則：  
  
-   欄位是必要或選擇性在序列。  
  
-   序列可能包含子序列，與子序列可能會重複序列中。  
  
-   您可以使用數種訊息類型中的欄位。  
  
-   在欄位中，可能會有項目或子欄位。 項目或子欄位可能是通用於數個欄位。  
  
-   群組節點代表每個重複的序列。  
  
-   每個欄位可能本身會有多個 nodal 等級，以記錄每個所述。  
  
-   結構描述項目代表只最低的層級子欄位。  
  
-   在一般和基底結構描述會定義一般記錄和項目。  
  
-   結構描述代表許多格式 （例如合作對象的欄位） 中的某些欄位。 結構描述會定義這類欄位做為選擇的欄位。  
  
-   某些欄位具有有限的一組值。 大部分的情況下，結構描述會列出這些值。 結構描述定義也包含字元集驗證。  
  
 此部分包含：  
  
-   [基底和通用結構描述](../../adapters-and-accelerators/accelerator-swift/base-and-common-schemas.md)  
  
-   [SWIFT 標頭和結尾結構描述](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
-   [SWIFT 結構描述命名慣例](../../adapters-and-accelerators/accelerator-swift/swift-schema-naming-conventions.md)