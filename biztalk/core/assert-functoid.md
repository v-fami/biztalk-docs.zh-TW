---
title: 判斷提示運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e91dac06-f909-4fb2-8c87-828a3dfe2c27
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03237c27e0e35642be197b549c8b0102d9350702
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230310"
---
# <a name="assert-functoid"></a>判斷提示運算質

## <a name="overview"></a>概觀
**Assert**運算質輸出的字串值或擲回例外狀況的布林值為基礎。 如果您將此運算質結合的一或多個**邏輯**運算質，您可以有效地測試對應中條件的相關假設。 例如，如果您有對應預期訂單訂單金額絕對不會超過特定閾值時，您可以測試訂單值使用**Greater Than**運算質，然後連接到**Assert**運算質。 如果 「 邏輯 」 運算質傳回**True**、 **Assert**運算質將會擲回例外狀況，使用您提供的字串。  
  
 ![判斷提示運算質](../core/media/assertfunctoid.gif "AssertFunctoid")  
  
## <a name="see-also"></a>另請參閱  
 **判斷提示運算質參考**和**邏輯運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]