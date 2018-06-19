---
title: 模組 6： 部署商務規則 |Microsoft 文件
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
ms.openlocfilehash: 8e890456b7ff3e467a0f513a261d12a52f92689f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207990"
---
# <a name="module-6-deploying-the-business-rules"></a>模組 6： 部署商務規則
這個模組中您部署商務規則，確認您的安裝記錄檔，並確認您的部署使用商務規則編輯器 」 工具。  
  
 您可以使用商務規則，確保[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]協會全球 Interbank 財務 Telecommunication (SWIFT) 標準中所定義的訊息遵守格式規格欄位規格，網路驗證規則。 格式規格屬於整個訊息的結構和欄位規格詳細說明每個訊息中的欄位。 網路驗證規則套用到欄位交互驗證，而複雜的本質。  
  
 A4SWIFT 提供每個訊息的 XSD 結構描述規格。 A4SWIFT 反組譯工具 (DASM) 和組譯工具 (ASM) 使用結構描述剖析或序列化和驗證原生的一般檔案訊息。 驗證只限於格式規格和結構描述編碼的欄位規格。 不過，您無法編碼某些格式和欄位在結構描述中相關的規則。  
  
 A4SWIFT 也包含一組遵循 SWIFT 標準發行指南 (SRG) 的商務規則。 BizTalk Server 商務規則引擎 (BRE) 呼叫 A4SWIFT 原則，並強制執行 A4SWIFT 商務規則。  
  
 這些商務規則會包含因為複雜的驗證與格式和欄位，以及已超出自然的結構描述功能的網路驗證規則。 SWIFT DASM 或 ASM 元件接收或傳送管線內呼叫 BRE。  
  
 您可以開啟或關閉的驗證藉由變更**BREValidation** DASM 您管線內的屬性。  
  
 此部分包含：  
  
-   [第 1 課： 部署相關的商務規則](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)  
  
-   [第 2 課： 確認部署使用 「 商務規則編輯器 」 工具](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)