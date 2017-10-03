---
title: "警告-找到自訂 XSLT 但沒有自訂延伸模組 XML |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.warning.customXsltButNoCustomExtensionXML
ms.assetid: af008ac2-e9ae-4753-a5ba-bf4dbb711a4e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b67591e0e0dbb6b3ecac9aee1566c3245c9969a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="warning---custom-xslt-but-no-custom-extension-xml"></a>警告-找到自訂 XSLT 但沒有自訂延伸模組 XML
**錯誤碼**  
  
 btm1034  
  
 **說明**  
  
 **自訂 XSLT 路徑**屬性但未覆寫**自訂延伸模組 XML**遭到覆寫的屬性。 若您是刻意這樣做，則可以略過此警告。  
  
 BizTalk 對應工具會使用指定的 XSLT**自訂 XSLT 路徑**屬性並且產生空的延伸模組 XML 對應檔案。 若要從外部組件提供的 XSLT 內呼叫，您必須指定檔案，使用**自訂延伸模組 XML**屬性，其中包含組件名稱對應的前置詞。  
  
 **使用者動作**  
  
 如果此警告所指定的條件不是有意的請提供相容值給**自訂延伸模組 XML**屬性或移除覆寫值**自訂 XSLT 路徑**屬性。