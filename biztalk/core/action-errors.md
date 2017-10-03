---
title: "動作錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cf0a5b-d1dd-4807-9660-e8a8b7012b40
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f25f1f15307077943ef370a335885690bea22c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="action-errors"></a>動作的錯誤
本節包含診斷及解決 WCF 動作錯誤的詳細的資訊。  
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|單一動作不能包含新行字元。 移除所有的新行字元。 或者，若要指定多個動作，使用動作對應語法。|  
  
## <a name="explanation"></a>說明  
 此錯誤表示傳送埠的 action 屬性中包含不允許新行字元。  
  
> [!NOTE]
>  動作已定義的對應時，則不適用這項限制。  
  
## <a name="user-action"></a>使用者動作  
 若要修正的 action 屬性中使用下列程序。  
  
 
1.  開啟 [BizTalk Server 管理] 。  
  
2.  在 主控台根目錄中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  選取**屬性**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  選取 **[設定]**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，選取**一般** 索引標籤。  
  
9. 在**SOAP 動作標頭**區段中，移除新行字元從**動作**文字方塊。  

## <a name="more-good-info"></a>良好的詳細資訊  
 如需有關動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../core/specifying-soap-actions-for-wcf-send-adapters.md)