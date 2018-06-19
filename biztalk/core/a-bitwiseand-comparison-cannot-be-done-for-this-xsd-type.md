---
title: BitwiseAnd 比較無法完成此 XSD 類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82bc2351-c002-458a-9d35-5fdcc91c6a0e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c0f3aa2b3ae7c60f3c104daaa885ab7ae8cc7ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224806"
---
# <a name="a-bitwiseand-comparison-cannot-be-done-for-this-xsd-type"></a>BitwiseAnd 比較無法完成此 XSD 類型
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|Err_InvalidBitwiseComparision|  
|訊息文字|BitwiseAnd 比較無法完成此 XSD 類型。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法將內容屬性做比較來決定訊息的批次嘗試時。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請在作用中批次中提供的篩選條件不會指定內容屬性具有無法位元比較 CSD 類型。