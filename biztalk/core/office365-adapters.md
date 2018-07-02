---
title: 使用 Office 365 Outlook 電子郵件配接器 |Microsoft Docs
description: 傳送和接收訊息在 BizTalk Server 中，包括電子郵件、 行事曆和連絡人中使用 Office 365 Outlook 配接器的概觀
ms.custom: ''
ms.date: 06/19/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: ribarua
manager: dougeby
ms.openlocfilehash: 2002ab6859a71a930ef9166f9b3a5a072ba77948
ms.sourcegitcommit: e7609c319b64ec20bf215d17aa5ac4f9dcae52ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36946176"
---
# <a name="office-365-outlook-adapters-in-biztalk"></a>在 BizTalk 中的 office 365 Outlook 配接器

## <a name="overview"></a>概觀
**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]功能套件 3**，您可以傳送和接收 BizTalk Server 和 Office 365 Outlook 的功能之間的訊息。 功能組件 3 包含下列配接器：

- [Office 365 Outlook 電子郵件配接器](office365-mail-adapter.md)
- [Office 365 的 Outlook 行事曆配接器](office365-calendar-adapter.md)
- [Office 365 Outlook 連絡人配接器](office365-contact-adapter.md)

## <a name="prerequisites"></a>必要條件

* 有[Office 365 帳戶](https://outlook.office365.com)
* 安裝[Feature Pack 3](https://aka.ms/bts2016fp3) BizTalk 伺服器上
* 使用的帳戶是 SSO 系統管理員群組的成員，

## <a name="tms-overview"></a>TMS 概觀

BizTalk Server TMS 是重新整理 BizTalk 使用 Office 365 OAuth 權杖的服務。 它會重新整理這些權杖，以定期確保，權杖永遠保持有效。 它會相依於企業單一登入服務 (ENT SSO)，並必須安裝在裝載主要密碼伺服器的電腦上。 

## <a name="install-biztalk-server-tms"></a>安裝 BizTalk Server TMS

1. 安裝[Feature Pack 3](https://aka.ms/bts2016fp3)。
2. 在  `\Program Files (x86)\Microsoft BizTalk Server <your version>`，執行 BizTalkTMS.msi。
3. 輸入使用者名稱和密碼之使用者的 SSO 系統管理員群組的成員。 

![BizTalk Server TMS 安裝程式](../core/media/BizTalk-TMS.png)

## <a name="sign-in-to-office-365"></a>登入 Office 365

當您要建立[傳送埠](how-to-create-a-send-port2.md)或是[接收位置](how-to-create-a-receive-location.md)在 BizTalk 管理中，您可以**登入...** 至 Office 365 帳戶：

  ![Office 365 登入](../core/media/office365-signin.png)

您輸入 Office 365 的認證，並確認權限。 這些認證授權 BizTalk 連接並存取 Office 365 帳戶。 在下列範例中，您會看到 Office 365 Outlook 行事曆的權限：

  ![Office 365 行事曆權限](../core/media/office365-calendar-permissions.png)

## <a name="get-started"></a>開始使用
安裝 BizTalk Server TMS 之後，您即可建立成品，並開始使用配接器：

- [Office 365 Outlook 電子郵件配接器](./office365-mail-adapter.md)
- [Office 365 的 Outlook 行事曆配接器](./office365-calendar-adapter.md)
- [Office 365 Outlook 連絡人配接器](./office365-contact-adapter.md)
