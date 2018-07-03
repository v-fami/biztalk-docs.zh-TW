---
title: 尋找開始項目時，找到結束項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7690744-a795-47cc-bc66-a0314a4cc320
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e200f4ffd8d822a5c2bb1a0bad74a60e84a408a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992429"
---
# <a name="an-end-element-was-found-while-looking-for-start-element"></a>尋找開始元素時找到結尾元素
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  產品名稱   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| 產品版本 |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    事件識別碼     |                                                 -                                                 |
|  事件來源   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI       |
|    元件    |                                            將 EDI 引擎                                             |
|  符號名稱  |                             EndElementFoundWhenLookingForStartElement                             |
|  訊息文字   | 名稱的 EndElement{0}找不到，以名稱尋找 StartElement 時{1}，深度 {2} |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，BizTalk Server 無法處理內送 XML 訊息 （之後剖析） 或外寄 XML 訊息 （在之前序列化） 因為 XML 訊息驗證失敗。 XML 訊息不包含標頭或資料元素結束標記。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，XML 訊息，並加入適當的結束標記或結尾，並再重新傳送訊息。