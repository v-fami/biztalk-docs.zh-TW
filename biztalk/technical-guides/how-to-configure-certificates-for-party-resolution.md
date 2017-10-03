---
title: "如何設定合作對象解析的憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 060101c1-14f3-4600-a18e-48a160d59bca
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 153c8ccce1fafbe32c51b1c048fad4081f5b0b0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-for-party-resolution"></a>如何設定合作對象解析的憑證
當您使用 BizTalk 總管 中建立合作對象時，您可以設定合作對象，以便使用數位簽章來解析合作對象。 如果您設定合作對象如此一來，當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]收到訊息時，它會使用公開金鑰憑證，來決定是誰傳送訊息，並在已知的合作對象解析寄件者[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
### <a name="to-configure-party-resolution-to-use-a-certificate"></a>若要設定合作對象解析，以使用憑證  
  
1.  開啟**合作對象屬性** 對話方塊。  
  
2.  按一下**憑證**索引標籤，然後再按一下**瀏覽**。  
  
3.  選取的憑證。  
  
4.  按一下 **[確定]**。