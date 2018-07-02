---
title: 資料元素太長 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf608cc1-d482-4e19-8f56-10d9e03feb79
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 134c2c2b0931373840cf5726d8f6680590840b9d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988735"
---
# <a name="data-element-too-long"></a>資料元素太長
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |                                 資料元素太長                                  |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線或 EDI 傳送管線無法處理內送交換，因為資料的項目已超過指定的結構描述的長度上限。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請縮短中已太長，讓它低於最大限制之交換的資料元素。 若要判斷最大長度，\XSD_Schema 資料夾中開啟結構描述、 搜尋資料的項目識別碼，並識別 maxLength 的值為何。