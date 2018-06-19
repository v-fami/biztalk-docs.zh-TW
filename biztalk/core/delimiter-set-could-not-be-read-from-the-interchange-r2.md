---
title: 無法讀取的分隔符號集從交換 (R2) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17bdd32e-d43f-4f59-af27-5d3054fd5432
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3836b218ac3596bef25edb29eaf72c38f65b6e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239078"
---
# <a name="delimiter-set-could-not-be-read-from-the-interchange-r2"></a>無法讀取的分隔符號集從交換 (R2)
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|無法從交換中讀取的分隔符號集。 從根節點遺漏 DelimiterSetSerializedData 屬性。|  
  
## <a name="explanation"></a>說明  
 此錯誤表示交換不包含分隔符號設定的值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   加入分隔符號設定的值交換，如下所示：  
  
    1.  開啟訊息。  
  
    2.  決定是否在交換沒有 UNA 區段。 如果不是 UNA 區段，要求的夥伴加入交換的 UNA 區段。  
  
-   輸入分隔符號值至 EfactDelimiters 管線屬性中，如下所示：  
  
    1.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，以滑鼠右鍵按一下使用您要設定屬性之管線的接收位置或傳送埠。 按一下 **[屬性]**。  
  
    2.  按一下要設定屬性之管線旁邊的省略符號按鈕 (?。  
  
    3.  UNA 分隔符號輸入值為逗號分隔清單 （適用於 UNA1、 UNA2、 UNA3、 UNA4、 UNA5、 和 UNA6），變更所需的預設值。 預設值如下： 0x3A、 0x2B、 0x2C、 0x3F、 0x20、 0x27。  
  
    4.  按一下 **[確定]**。