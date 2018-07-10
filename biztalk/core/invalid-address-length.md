---
title: 無效的位址長度 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8e16eb6-e77e-4361-ac91-0730004c4433
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8da5e041ad861557817491695f0d7972a207864a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008471"
---
# <a name="invalid-address-length"></a>無效的位址長度
## <a name="details"></a>詳細資料  

|                 |                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------|
|  產品名稱   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| 產品版本 |                 [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                  |
|    事件識別碼     |                                              0                                              |
|  事件來源   |                                              0                                              |
|    元件    |                                              0                                              |
|  符號名稱  |                                              0                                              |
|  訊息文字   | 無效的位址長度;指定位址長度為{0}字元的限制是{1}字元 |

## <a name="explanation"></a>說明  
 您所提供超過 255 個字元，WCF 傳輸的最大長度的位址。 這是由 BizTalk Server，不是由 WCF 所加諸的限制。  

## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定有效的位址。  

#### <a name="to-configure-a-valid-address"></a>若要設定有效的位址  

1. 按一下 **開始**，按一下**所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理]**。  

2. 在 [主控台根目錄中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，然後展開**應用程式**。  

3. 找出您的應用程式，然後找出您的傳輸。  

4. 以滑鼠右鍵按一下傳輸名稱。  

5. 按一下 **[屬性]**。  

6. 在 連接埠**型別**清單中，選取正確的連接埠。  

7. 按一下 **設定**。  

8. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。  

9. 在 **位址 (URI)** 文字方塊中，確認位址不能超過 255 個字元的最大長度。
