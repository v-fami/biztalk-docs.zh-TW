---
title: "設定位移量驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- amounts, validating
- validating, amounts
- amounts, offsets
- offsets
ms.assetid: 39d5510c-52e6-4fd9-9632-582b508f04d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaa41714cbe5c3baba85e82f2992ff72544c425c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-offsets-for-amount-validation"></a>設定位移量驗證
在訊息類型 MT102，MT103，以及 MT103PLUS 量欄位的使用方式規則會驗證其各自的驗證原則中的規則。 數量欄位可以完全相符，或是可驗證的金額的範圍內。  
  
 若要啟用驗證的範圍內，您可以指定位移的百分比在相關的驗證原則中的方法呼叫中。 例如，如果您設定欄位的金額為 100，位移的百分比為 10%，有效的金額會 110 （含) 到 90 的任何值。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]提供這項支援 MT102、 MT102PLUS 和 MT103 訊息類型。  
  
 在指定位移的百分比**IsValidSettlementAmount**或**IsValidInterbankSettledAmount**驗證原則中的方法。 **IsValidSettlementAmount**方法會實作 MT102 和 MT102PLUS 訊息量欄位的使用方式規則。 **IsValidInterbankSettledAmount**方法會實作 MT103 訊息量欄位的使用方式規則。 您 OffsetPercent 引數，也就是其中一個這些方法的第十個引數中指定位移的百分比。  
  
 百分比位移設定時，套用至下列欄位：  
  
|訊息類型|位移通過驗證的欄位|  
|------------------|-----------------------------------|  
|MT102 或 MT102PLUS|32<br /><br /> 33B|  
|MT103|19，順序 C<br /><br /> 31A，順序 C<br /><br /> 72 G|  
  
### <a name="to-set-an-offset-percentage"></a>若要設定位移的百分比  
  
1.  開啟文字編輯器，例如 [記事本]。  
  
2.  在編輯器中，瀏覽至您要設定位移的百分比的訊息驗證原則的位置。 例如，您可以找到訊息驗證原則 MT103 訊息類型，MT103_Validation_Policy.xml，在*\<磁碟機 >*: files\ Microsoft BizTalk Accelerator for SWIFT\<版本> 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Category 1\MT103。 開啟 驗證原則。  
  
3.  在原則中，搜尋上 IsValidSettlementAmount MT102 和 MT102PLUS 訊息或 IsValidInterbankSettledAmount MT103 訊息。  
  
4.  向下計數的第十個引數。 輸入引數中的位移的百分比。  
  
5.  儲存檔案，然後關閉編輯器。