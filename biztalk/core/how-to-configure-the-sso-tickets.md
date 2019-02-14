---
title: 設定 SSO 票證 |Microsoft Docs
description: 使用 SSO 管理或命令列來允許及驗證企業單一登入票證系統層級，以及在 BizTalk Server 中的分支機構應用程式。
ms.custom: ''
ms.date: 01/08/2019
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO], configuring tickets
- SSO, tickets
- tickets [SSO], configuring
ms.assetid: 32f0384b-ac79-4cce-b3f5-f4f8a73a673a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3abac3a0d527c6834105db8fd1c74fd934fd821d
ms.sourcegitcommit: 41947648c73d437a201b2190307e0270d61e037a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56087930"
---
# <a name="configure-the-sso-tickets-in-biztalk-server"></a>在 BizTalk Server 中設定 SSO 票證
針對整個單一登入系統，您可以使用企業單一登入 (SSO) 管理的 MMC 或命令列，以控制票證行為。 使用此工具，您就可以允許票證，並驗證 SSO 票證。  
  
## <a name="before-you-begin"></a>開始之前

- 如果遠端電腦上安裝 SSO 管理，您可以執行遠端[IssueTicket](https://docs.microsoft.com/biztalk/core/technical-reference/issoticket-issueticket-method)作業。 SSO 管理模組和執行階段模組 （ENTSSO 服務） 之間的所有流量都會都加密。  
  
- 使用 ssomanage.exe 命令列公用程式，您可以輸入分支機構應用程式層級的票證逾時。 只有在進行應用程式的更新時，會建立應用程式時，不時，您可以這麼做。
  
- 在 SSO 系統層級與分支機構應用程式層級，只有 SSO 系統管理員群組的使用者，才可以設定票證。  
  
- 如果在系統層級停用票證，它不能在分支機構應用程式層級。 您可在系統層級中啟用票證和分支機構應用程式層級停用它們。  
  
- 如果驗證已啟用在系統層級，則必須驗證票證，分支機構應用程式層級。 可以停用在系統層級的驗證，並啟用分支機構應用程式層級。  
  
- 如果您輸入票證逾時的系統層級和分支機構應用程式層級，輸入分支機構應用程式層級會決定票證到期時間。  
  
如需有關票證和票證驗證的詳細資訊，請參閱 < [SSO 票證](../core/sso-tickets.md)。  
  
## <a name="allow-affiliate-application-tickets-using-sso-administration"></a>允許使用 SSO 管理分支機構應用程式票證  
  
1.  從**開始**功能表上，選取**所有程式** > **Microsoft 企業單一登入** > **SSO 管理**.
  
2.  在 範圍 窗格的 ENTSSO MMC 嵌入式管理單元，依序展開**分支機構應用程式**節點。  
  
3.  以滑鼠右鍵按一下**分支機構應用程式** > **屬性**。  
  
4.  選擇**選項** 索引標籤。  
  
5.  選取 **允許票證**並輸入您想要的票證逾時。  
  
## <a name="allow-and-validate-sso-system-level-tickets-using-the-command-line"></a>允許和驗證使用命令列的 SSO 系統層級票證  
  
1. 開啟命令提示字元 ([開始] 功能表 > 型別**命令提示字元**> 選取**命令提示字元**)。

    > [!TIP]
    >  在系統上可支援使用者帳戶控制 (UAC)，您可能需要系統管理權限開啟命令提示字元 (以滑鼠右鍵按一下**命令提示字元** > **系統管理員身分執行**)。
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是`\Program Files\Common Files\Enterprise Single Sign-On`。 例如，輸入： 

    `cd C:\Program Files\Common Files\Enterprise Single Sign-On`
  
3. 型別`ssomanage -tickets <allowed yes/no> <validate yes/no>`，其中 *\<允許是/否\>* 指出，是否允許票證以及 *\<驗證是/否\>* 指出是否需要它們正在兌換之後驗證票證。  
  
    您可以使用`yes`， `no`， `on`，或`off`允許和/或驗證票證。 這些字與大小寫無關，不論您的語言設定為何都必須使用。
  
## <a name="see-also"></a>另請參閱

[了解 SSO](../core/understanding-sso.md)   
[使用 SSO](../core/using-sso.md)
