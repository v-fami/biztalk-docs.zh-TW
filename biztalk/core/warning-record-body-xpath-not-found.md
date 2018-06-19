---
title: 警告-找不到記錄 Body XPath |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.recordBodyXPathNotFound
ms.assetid: d46e0732-08ce-4292-84d8-56dc020063e2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebd6640aa469fe9383b615d70235ab488c8798f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288102"
---
# <a name="warning---record-body-xpath-not-found"></a>警告-找不到記錄 Body XPath
**錯誤碼**  
  
 BEC1008  
  
 **說明**  
  
 **Body XPath**空找不到此信封結構描述中指定的根節點的屬性或參考不存在的節點。 信封結構描述所指定**信封**屬性**結構描述** 節點，必須要有有效的值**Body XPath**屬性指定的根目錄結構描述中的 參考 節點。  
  
 如果沒有根參考節點以指定**根參考**屬性**結構描述**節點，第一個根節點在結構描述中，預設根參考節點，必須要有其中是有效的值**Body XPath**屬性。 **Body XPath**屬性值可用來識別每個在信封內所包含的訊息結構描述。  
  
 **使用者動作**  
  
 選取指定的根節點，然後選取 值**Body XPath**正確識別關聯的訊息內文的結構描述的屬性。