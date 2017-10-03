---
title: "無法建立繫結組態項目進行編輯 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71853662-5a4a-417e-8160-c93dbcbea336
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5c4387e0cb9287ecc4d491291fdfd1fa6b79ab9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-binding-configuration-element-for-editing"></a>無法建立繫結組態項目進行編輯
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法建立繫結組態項目進行編輯。 請檢查 BindingType] 和 [BindingConfiguration 屬性的值。|  
  
## <a name="explanation"></a>說明  
 載入使用者介面中顯示的資料繫結項目時發生錯誤。 使用自訂繫結通常會發生這個錯誤。 繫結項目可能遺失的組態檔中，因此並沒有出現在下拉式清單，以繫結。  
  
## <a name="user-action"></a>使用者動作  
 檢查值**BindingType**和**BindingConfiguration**屬性。  
  
 如需建立繫結組態項目詳細資訊，請參閱下列資源：  
  
-   [設定 Wcf-netmsmq 配接器](../core/configuring-the-wcf-netmsmq-adapter.md)