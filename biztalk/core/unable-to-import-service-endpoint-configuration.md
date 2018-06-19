---
title: 無法匯入服務端點組態。 | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dae5154-04e2-4d9b-b2b2-85313683fd9e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4100435706ab26c0f4ab99dea4d2088ecad1c948
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286718"
---
# <a name="unable-to-import-service-endpoint-configuration"></a>無法匯入服務端點組態。
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法匯入服務端點組態|  
  
## <a name="explanation"></a>說明  
 可能有多個說明這個錯誤。 組態檔可能包含無效的字元。 根項目可能已遺失。 根層級的資料可能不正確。  
  
## <a name="user-action"></a>使用者動作  
 請確認組態檔的有效性。 嘗試使用服務組態編輯器中開啟組態檔 (**svcConfigEditor.exe**)，並確認每個屬性。