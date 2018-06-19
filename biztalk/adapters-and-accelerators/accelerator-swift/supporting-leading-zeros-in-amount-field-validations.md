---
title: 支援前置 0 量欄位驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- amounts, amount fields
- amounts, leading zeros
- validating, amount fields
ms.assetid: 7c202422-019f-43da-9c2a-4b9fdf0b2859
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3559b63ec7588fa2d7451779947a476cf19b7bf0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961364"
---
# <a name="supporting-leading-zeros-in-amount-field-validations"></a>支援前置 0 量欄位驗證
某些訊息類型的驗證原則數量欄位上執行驗證。 若要啟用數量 欄位中的前置零，您必須編輯訊息類型的驗證原則。 您可以建立新版本的預設的驗證原則，並編輯 [商務規則編輯器] 中的引數，或在部署原則之前，您可以編輯預設原則，以手動方式在文字編輯器。  
  
 下表列出啟用或停用前置零的方法。 此資料表也會指出您需要設定的方法中引數的序數。 將它設定為 true 以啟用前置零，或設為 False 可停用它們。  
  
|方法|引數數目|  
|------------|---------------------|  
|**CheckValidAmount**|6|  
|**CheckCurrencyAmount**|4|  
|**CheckValidSignCurrencyAmount**|3|  
|**CheckValidSignDateCurrencyAmount**|4|  
|**IsValidTransactionDetailsCurrencyAmount**|4|  
  
 上表中的每個方法都包含在一個或多個訊息驗證原則。 若要在原則中設定引數，您必須搜尋上以確認原則是否包含它的方法名稱。 一種方法可能會多次出現在訊息的原則。  
  
### <a name="to-enable-or-disable-leading-zeros"></a>若要啟用或停用前置的零  
  
1.  開啟文字編輯器，例如 [記事本]。  
  
2.  在編輯器中，瀏覽至您要啟用或停用前置零的訊息驗證原則的位置。 例如，您可以找到訊息驗證原則 MT103 訊息類型，MT103_Validation_Policy.xml，在*\<磁碟機\>*: / 程式檔案/Microsoft BizTalk Accelerator for SWIFT/SWIFT 訊息/ 類別 1/MT103。 開啟 驗證原則。  
  
3.  在原則中，搜尋上**CheckValidAmount**方法。  
  
4.  如果您發現此方法，倒數計時適當的引數。 例如，對於**CheckValidAmount**方法，向第六個引數的計數。 將引數設**True**啟用前置的零或為 False，則停用它們。  
  
5.  重複步驟 3 和 4 上表中每個方法。  
  
6.  儲存檔案，然後關閉編輯器。