---
title: "協議解析根據內容屬性失敗，通訊協定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58fccd84-579c-4b5e-872b-33730d4079e8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76d74ad7aa4a73f4a0befcef32bc8051195cb080
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-based-on-the-context-properties-for-protocol-has-failed"></a>無法解析通訊協定根據內容屬性的協議
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|AgreementResolutionContextPropertiesLookupFailed|  
|訊息文字|協議解析根據 {0} 通訊協定失敗的內容屬性。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析為協議，根據客戶所提供的內容屬性。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請提供的內容屬性做為 BizTalk 訊息的一部分，可能是協議解析。