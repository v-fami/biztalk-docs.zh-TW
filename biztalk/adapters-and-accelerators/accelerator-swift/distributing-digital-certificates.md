---
title: 散發數位憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- digital signatures
- security, digital signatures
ms.assetid: 3e93a405-3c9b-43f5-bbdf-bec25d43eb45
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486a1f45dc6a570bab6518eef215f4133015ead5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209414"
---
# <a name="distributing-digital-certificates"></a>散發的數位簽章
用於數位簽章的數位簽章通常發行和發佈至使用者工作站憑證授權單位 (Ca)，可能是外部的商業實體，例如 VeriSign 或裝載於組織的內部 Ca。 使用數位簽章的類型 （加密演算法和加密強度） 可能與組織的不同。 [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]數位簽署表單使用所組成的私密金鑰，且具有數位簽章和/或金鑰使用方法屬性的加密值的任何憑證格式。 此外，憑證的用途應該被設定為用戶端驗證。  
  
 數位憑證的主要目的是找出使用該憑證來數位簽署文件和建立加密的單程雜湊的文件資料的使用者。 登入後的加密雜湊資料偵測到的任何資料的變更 （如果資料已變更，它會產生相同雜湊）。 數位簽章所發出的網域使用者帳戶和角色為基礎 (或[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]網域群組)，特定使用者的受保護的和[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證和使用者登入機制。 您可以使用數位簽章，特別是讓您根據發行數位簽署文件您[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]網域使用者帳戶。  
  
 SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] A4SWIFT 所提供的 FormGenerator 公用程式產生的表單需要您以數位方式簽署 （或副署） 表單，每當您嘗試將訊息提交給 A4SWIFT Message Repair 和 New Submission 時 (透過[!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)])。 您無法避開這項需求[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]。 不過，您可以移[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]完全與寫入訊息直接 （假設您擁有適當的認證來存取 SharePoint Web 資料夾） 的 SharePoint Web 資料夾。 不過，如果訊息不包含有效的數位簽章，Message Repair 和 New Submission 立即會拒絕訊息做為安全性錯誤。  
  
 訊息修復和 New Submission 元件必須能夠存取數位憑證訊息中使用的公開金鑰，才能修復工作流程。 若要啟用 Message Repair 和 New Submission 的存取權的公開金鑰的憑證。 每一位使用者必須位於其他人存放區中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]裝載 Message Repair 和 New Submission 協調流程服務的電腦。  
  
> [!NOTE]
>  訊息修復和新送出工作流程中使用憑證和使用者設定訊息修復必須由例如 VeriSign 或 e 信任的受信任的憑證授權單位發行。  
  
 特定如何設定內部 Ca 的詳細資訊，請參閱 「 設定總憑證授權單位 」，在 MSDN 網站上[http://go.microsoft.com/fwlink/?LinkId=48688](http://go.microsoft.com/fwlink/?LinkId=48688)。