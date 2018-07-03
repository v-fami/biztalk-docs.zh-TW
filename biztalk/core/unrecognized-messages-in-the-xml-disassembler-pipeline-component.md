---
title: 無法辨識的訊息，在 XML 解譯器管線元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Allow Unrecognized Messages property
- XMLNorm.AllowUnrecognizedMessage property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], unrecognized messages
ms.assetid: 5a6be3a8-0bac-426a-bf0b-5091191091de
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c7df0ea8abe05f866d5cb4f9fb86d85083e1690
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987663"
---
# <a name="unrecognized-messages-in-the-xml-disassembler-pipeline-component"></a>XML 解譯器管線元件中無法辨識的訊息
XML 解譯器元件在以下情況中可能會將訊息當作「無法辨識」處理：  
  
- 已接收的 XML 訊息沒有內文、空的內文或內文中為空白資料。  
  
- XML 訊息已接收，但是沒有部署其結構描述。  
  
  根據處理無法辨識的訊息**允許無法辨識的訊息**屬性 (或在**XMLNorm.AllowUnrecognizedMessage**訊息內容屬性)。  
  
  如果**允許無法辨識的訊息**設為 **，則為 True**，會發生下列情況：  
  
- 沒有內文、空白/空值的內文，或內文中的資料為空白/空值的訊息會透過 XML 解譯器未經變更傳送出去。  
  
- 沒有相關聯的已部署結構描述之 XML 文件會透過 XML 解譯器未經變更傳送出去。  
  
- 無論是在元件屬性中明確參考結構描述或是在結構描述解析程序期間找到結構描述，具有相關聯的已部署結構描述之 XML 文件都是由 XML 解譯器處理。  
  
  如果**允許無法辨識的訊息**設為**False**，會發生下列情況：  
  
- 沒有內文、空白/空值的內文，或內文中的資料為空白/空值的訊息不會透過 XML 解譯器傳送出去。  
  
- 沒有相關聯的已部署結構描述之 XML 文件不會透過解譯器傳送出去。 如有可能，會報告錯誤並暫停訊息。  
  
- 無論是在元件屬性中明確參考結構描述或是在結構描述解析程序期間找到結構描述，具有相關聯的已部署結構描述之 XML 文件都是由 XML 解譯器處理。  
  
  依照預設，XML 解譯器不允許無法辨識的訊息。  
  
> [!NOTE]
>  非 XML 訊息不會處理 XML 解譯器，不論**允許無法辨識的訊息**屬性設定。  
  
## <a name="see-also"></a>另請參閱  
 [XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md)   
 [如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)