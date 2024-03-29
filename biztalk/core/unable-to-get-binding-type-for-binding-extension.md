---
title: 無法取得繫結型別繫結延伸模組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a7cfc81-7439-48f9-8cac-42b2419ecd9d
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdf0e0fd1ebf88c9231d70e9102d76fa67157cb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006231"
---
# <a name="unable-to-get-binding-type-for-binding-extension"></a>無法取得繫結延伸模組的繫結類型
## <a name="details"></a>詳細資料  

|                 |                                                                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                        |
| 產品版本 |                                                                                    [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                    |
|    事件識別碼     |                                                                                                                0                                                                                                                 |
|  事件來源   |                                                                                                                0                                                                                                                 |
|    元件    |                                                                                                                0                                                                                                                 |
|  符號名稱  |                                                                                                                0                                                                                                                 |
|  訊息文字   | 無法取得繫結型別繫結延伸模組 」{0}"。 如果您的應用程式開啟時，已更新 machine.config，重新啟動您的應用程式，以反映變更。 確認繫結延伸模組已註冊在 machine.config 中 |

## <a name="explanation"></a>說明  
 未正確設定 Wcf-custom 或 Wcf-customisolated 傳輸的自訂繫結延伸模組。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一或多個項目：  

- 請確定**machine.config 檔案**中 **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config**具有\< **bindingExtensions** \>正確設定的項目。  

- 在 Windows 檔案總管中，移至 **%WinDir%\Assembly**，並確定實作自訂繫結延伸模組的組件是否已正確安裝。  

- Wcf-custom 配接器在 BizTalk 管理主控台中，重新啟動執行的 WCF 傳輸主控件執行個體。  

- Wcf-customisolated 配接器，在 [IIS 管理] 主控台中，重新啟動應用程式集區裝載的 WCF 傳輸。  

- 開啟和關閉 BizTalk 管理主控台中，如果已開啟  

  如需詳細資訊，請參閱下列資源：  

- [如何啟用 WCF 擴充性點，WCF 配接器](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)
