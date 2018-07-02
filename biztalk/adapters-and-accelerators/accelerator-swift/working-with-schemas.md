---
title: 使用結構描述 |Microsoft Docs
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
ms.openlocfilehash: cb6ac17cd0959d712da290b937a961d517f320e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968359"
---
# <a name="working-with-schemas"></a>使用結構描述
在 Microsoft 所提供的結構描述[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]是全球 Interbank 財務電信 (SWIFT) FIN 訊息協會 Microsoft XSD 表示法。 每個訊息類型都有自己的結構描述，包括 SWIFT 標頭和 SWIFT trailer （交換格式）。 此結構描述是不足，無法傳送或接收 SWIFT 的訊息。 這些結構描述是唯一的分隔和位置記錄，以提供詳細的 XML 表示法，一般檔案 FIN 結構的混合。  

 SWIFT 的大部分客戶會使用相對較小的子集的 SWIFT FIN 訊息。 若要實作對於這些客戶的方案，您可以建立 BizTalk 結構描述專案 (如所示[模組 2： 加入新的結構描述專案](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md)A4SWIFT 教學課程的)。 新增相關的訊息結構描述 (MT*xxx*.xsd) 從\\\ Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category x\MT xyy 目錄，其中 x 是 FIN 訊息類型的第一個數字，而 xyy 是訊息的三位數的訊息類型。  

 您可以將數個結構描述加入相同的專案。 若要維護管理能力，您不應該新增 20 個以上的訊息結構描述，每個專案。 您也需要將基底和通用的結構描述加入至專案。 如果您已部署之基底和通用結構描述，您要建立其組件的參考，而不是將其部署。 本章節描述這些結構描述。 訊息結構描述已準備好使用，因為是傳送至 SWIFT 的網路訊息和接收自 SWIFT 的訊息。  

 您可以檢查在 Microsoft 中的每個 SWIFT 結構描述的內容[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]使用結構描述編輯器。 所有訊息交換的結構描述有下列的一般結構：  

- 標頭  

- 訊息文字  

- 結尾  

  本章節描述的標頭和結尾結構描述。 訊息文字包含 FIN 訊息的承載，並包含的所有資料欄位包含寄件者、 接收者和訊息型別欄位除外。 這三個欄位都包含在標頭部分。 有些訊息也包含選擇性的使用者標頭，也會提供處理資訊。  

  每個 FIN 訊息內容是由一系列已定義的序列中的欄位所組成。 這些欄位會符合下列規則：  

- 欄位可能是必要或選擇性序列內。  

- 序列可能包含子序列，並在順序中可能重複的子序列。  

- 您可以使用數種訊息類型中的欄位。  

- 在欄位中可能有項目或子欄位。 項目或子欄位可能是通用於數個欄位。  

- 群組節點代表每個重複的序列。  

- 每個欄位可能本身有多個 nodal 層次，每個描述為一筆記錄。  

- 結構描述項目代表只有最低層級子欄位。  

- 一般和基底結構描述定義一般記錄和項目。  

- 結構描述代表某些欄位，以數種格式 （例如合作對象的欄位）。 結構描述會定義這類欄位，為選項欄位。  

- 某些欄位具有有限的一組值。 大部分的情況下，結構描述會列出這些值。 結構描述定義也包含字元集驗證。  

  此部分包含：  

- [基底和通用結構描述](../../adapters-and-accelerators/accelerator-swift/base-and-common-schemas.md)  

- [SWIFT 標頭和結尾結構描述](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  

- [SWIFT 結構描述命名慣例](../../adapters-and-accelerators/accelerator-swift/swift-schema-naming-conventions.md)
