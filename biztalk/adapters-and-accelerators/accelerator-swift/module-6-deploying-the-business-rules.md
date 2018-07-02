---
title: 模組 6： 部署商務規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorial, deploying business rules
- deploying, business rules
- business rules
ms.assetid: e8fb8993-3450-4795-80fd-ff28bff8fe97
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 389d8038b5a216f90d85399eeefaebde86284c71
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972839"
---
# <a name="module-6-deploying-the-business-rules"></a>模組 6： 部署商務規則
在這個模組中，您可以部署 商務規則，確認您的安裝記錄檔，並確認您使用 「 商務規則編輯器 」 工具的部署。  
  
 您可以使用商務規則來確保 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]協會全球 Interbank 財務電信 (SWIFT) 標準中所定義的訊息遵守格式規格欄位規格，驗證的網路規則。 格式規格屬於整個訊息的結構和欄位規格會詳細說明每個訊息中的欄位。 網路驗證規則套用到欄位交互驗證，而且在本質上複雜。  
  
 A4SWIFT 提供每個訊息的 XSD 結構描述規格。 A4SWIFT 反組譯工具 (DASM) 和組譯工具 (ASM) 使用的結構描述來剖析或序列化及驗證原生的一般檔案訊息。 驗證受限於格式規格和欄位規格的結構描述編碼。 不過，您無法將某些格式的編碼，並欄位在結構描述中的相關的規則。  
  
 A4SWIFT 也包含一組遵循 SWIFT 標準版指南 (SRG) 的商務規則。 BizTalk Server 商務規則引擎 (BRE) 呼叫 A4SWIFT 原則，並強制執行 A4SWIFT 的商務規則。  
  
 這些商務規則會包含因為格式和欄位，以及已超出的結構描述的自然功能的網路驗證規則相關的複雜驗證項目。 SWIFT DASM 或 ASM 元件接收或傳送管線內呼叫 BRE。  
  
 您開啟或關閉驗證變更**BREValidation** DASM 您管線內的屬性。  
  
 此部分包含：  
  
-   [課程 1：部署相關商務規則](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)  
  
-   [課程 2：使用商務規則編輯器工具確認部署](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)