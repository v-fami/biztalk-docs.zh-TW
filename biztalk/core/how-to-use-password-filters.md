---
title: 如何使用密碼篩選器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb429f8b-c301-45a3-8a4f-bbe6f2c566a3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ad35e2c3bec5b2ece69911b8de8c7fd13c9b790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255934"
---
# <a name="how-to-use-password-filters"></a>如何使用密碼篩選條件
「ENTSSO 密碼同步處理」功能，可以同步處理 Microsoft Windows Active Directory 和非 Windows 系統之間的密碼。 然而，許多外部系統都有不同於 Active Directory 的密碼原則需求 (例如，某個 IBM 系統可能會要求密碼都為大寫，而且僅限於 8 個字元)。這樣便會強制 ENTSSO 在兩個系統之間使用「最低公分母」來限制密碼安全性。  
  
 「ENTSSO 密碼篩選」功能可解決這項限制。 其實「密碼篩選」只是定義了額外屬性的「密碼同步配接器」。 這些其他屬性 (例如最大或最小長度、大小寫，以及字元限制) 會用來篩選密碼，以確保密碼符合外部系統的條件。  
  
 請注意，當您建立「密碼篩選」時，指定的系統管理員群組會自動當做「SSO 系統管理員帳戶」。 如果您變更 SSO 系統管理員群組，您必須確定密碼篩選器也會更新與新的 SSO 系統管理員帳戶。  
  
> [!NOTE]
>  就像 ENTSSO 系統中的所有項目，「密碼篩選」包含高度機密資訊，因此應盡可能地只讓最少數的人員知道。  
  
### <a name="to-create-a-password-filter"></a>若要建立密碼篩選  
  
1.  在**SSO 管理 主控台**，以滑鼠右鍵按一下**密碼管理**節點，然後再按一下**建立篩選**。  
  
     **密碼篩選精靈**隨即出現。  
  
2.  請依照精靈的指示來建立密碼篩選。  
  
### <a name="to-assign-an-affiliate-application-to-a-password-filter"></a>若要將分支機構應用程式指派至密碼篩選  
  
1.  以滑鼠右鍵按一下適當的篩選器，然後按一下**指派**...  
  
2.  選取適當**分支機構應用程式**。