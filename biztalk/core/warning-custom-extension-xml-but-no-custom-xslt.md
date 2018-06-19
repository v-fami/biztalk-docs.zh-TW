---
title: 警告-自訂延伸模組 XML 但找不到自訂 XSLT |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.warning.customExtensionXmlButNoCustomXSLT
ms.assetid: 3219c73c-2e58-4fe2-bc6e-2d60348d2415
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b626f8ede3231c04ae74dc0097cbdf524c90522
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288222"
---
# <a name="warning---custom-extension-xml-but-no-custom-xslt"></a>警告-自訂延伸模組 XML 但找不到自訂 XSLT
**錯誤碼**  
  
 btm1033  
  
 **說明**  
  
 **自訂延伸模組 XML**屬性但未覆寫**自訂 XSLT 路徑**遭到覆寫的屬性。 若您是刻意這樣做，則可以略過此警告。  
  
 BizTalk 對應工具將使用產生的 XSLT (透過編譯對應)，也將產生延伸模組 XML 並將它附加到自訂延伸模組 XML (由覆寫屬性所指定)。 這有助於進行對應包含**指令碼處理**運算質使用內嵌 XSLT 或內嵌 XSLT 呼叫範本，讓外部組件中的一個或多個方法的呼叫。 在這種情況下，使用者可以接著指定組件名稱對應中的前置詞**自訂延伸模組 XML**屬性。  
  
 **使用者動作**  
  
 如果此警告所指定的條件不是有意的請提供相容值給**自訂 XSLT 路徑**屬性或移除覆寫值**自訂延伸模組 XML**屬性。