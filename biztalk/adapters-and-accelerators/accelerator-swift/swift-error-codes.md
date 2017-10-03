---
title: "在 BizTalk Server 中的 SWIFT 錯誤碼 |Microsoft 文件"
description: "SWIFT 加速器，BizTalk Server 中的檢視類別和驗證類型"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03699986-965b-4a28-ab2e-09f110fb4db6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6d8e027eb9cce1cf66342484070310141e10b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-error-codes"></a>SWIFT 錯誤碼
SWIFT 定義許多網路造成的驗證，針對財務 (FIN) 訊息組。 每個驗證與檢查訊息的內容類型，然後傳回三個字元的錯誤碼與相關聯。 錯誤的程式碼的第一個字元隱含偵測到問題的類別，而值為字母。 其餘的兩個字元代表的 （結合類別） 時的錯誤詳細資料，並且一律會顯示為兩位數的程式碼。  

## <a name="class-of-errors"></a>類別的錯誤  
 下表列出的字母指定、 驗證類型，與每個錯誤，類別相關聯的規則變更和錯誤的類別是否支援。  
  
|類別|驗證類型和規則的變更|支援？|  
|-----------|-------------------------------------|----------------|  
|**C，D，E**|語意驗證規則 0 299|支援|  
|**Knn**|無效的程式碼文字欄位中*nn*|支援|  
|**M50**|訊息長度超過|不支援|  
|**M60**|遇到非 SWIFT 字元|支援|  
|**T**|文字驗證錯誤代碼|支援|  
|**G**|訊息的使用者群組 （咖啡杯） Textval 規則的特定錯誤代碼|不支援|  
|**B**|加值型服務的特殊的錯誤代碼|不支援|  
  
 中應參考所有 SWIFT 錯誤*SWIFT 使用者手冊*。 如需詳細資訊以及 SWIFT 錯誤碼的完整清單，請參閱*訊息格式的驗證規則*數量*SWIFT 使用者手冊*。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]此發行集的 2003 年 9 月版本中實作的規則。 您可以存取位於 SWIFT 網站[http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885)。  

## <a name="validation-errors"></a>驗證錯誤  
 有一些定義 A4SWIFT 的代碼。 這些錯誤碼會用於建立和實作 A4SWIFT，因此沒有對應的錯誤程式碼為這類規則 SWIFT 所定義的驗證/網路規則。 下表顯示的錯誤碼和錯誤會擲回對應的大小寫。 是的特定欄位，會擲回錯誤。  
  
|錯誤碼|Description|  
|----------------|-----------------|  
|A4SWIFT001|多行欄位的第一個字元不可為 ':' 或 '-' 字元的第二個和後續的行。|  
|A4SWIFT002|欄位包含無效的值。|  
  
> [!NOTE]
>  [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]包含支援某些舊版的訊息，因為內部應用程式可能會使用這些訊息。 因此，A4SWIFT 維護相關聯的 SWIFT 規則和錯誤碼。

## <a name="more-good-info"></a>良好的詳細資訊
[疑難排解： 問題與解決方式](troubleshooting-issues-and-resolutions1.md)  
[已知問題](known-issues5.md)  
[一般詞彙和定義](glossary6.md)