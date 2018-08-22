---
title: 錯誤-運算質固定輸入不相符 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.functoidFixedInputMismatch
ms.assetid: d235e7c3-efcf-4128-aef7-cdfdf1f317be
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85f9158bc7c648da5a70f19e3b8b48e6c6f7294a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017906"
---
# <a name="error---functoid-fixed-input-mismatch"></a>錯誤-運算質固定輸入不相符
**錯誤碼**  

 btm1010  

 **說明**  

 指出的運算質未指定正確的輸入參數數目。 輸入參數的數目必須與指定的相同。  

 **使用者動作**  

 使用下列一或多種方式，針對指定的運算質提供指定數目的輸入參數，應特別注意輸入參數的順序：  

- 若要建立其他連結，請使用拖曳方式在指定的運算質與來源結構描述中之節點或其他運算質之輸出間建立連結，這些節點位於指定運算質左邊的地圖格線頁中。  

- 若要建立其他連結，請選取指定的運算質，按一下省略符號 (**...**) 按鈕相關聯**輸入參數**中的屬性[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後設定並重新安排輸入參數順序**設定\<運算質\>運算質** 對話方塊。 您可以在此對話方塊中建立常數輸入參數、賦予這些參數值，並使用相對於其他輸入參數的順序排列這些參數。  

- 若要移除現有連結，每個連接至指定的運算質左邊連結上按一下滑鼠右鍵然後**刪除**。  

- 若要移除現有連結，選取指定的運算質，請按一下省略符號 (**...**) 按鈕相關聯**輸入參數**中的屬性[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後在**設定\<運算質\>運算質**對話方塊中，刪除所有輸入參數，選取並按一下![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete")為每個按鈕。 您必須使用此方式來刪除常數輸入參數。
