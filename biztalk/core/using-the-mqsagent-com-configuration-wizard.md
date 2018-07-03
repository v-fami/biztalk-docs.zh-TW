---
title: 使用 [MQSAgent COM + 組態精靈] |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mqsagent.wizard
helpviewer_keywords:
- MQSeries adapters, MQSAgent COM+ Configuration Wizard
- configuring [MQSeries adapters], MQSAgent COM+ Configuration Wizard
- MQSAgent COM+ Configuration Wizard
ms.assetid: f106700a-7f57-4c83-9344-6525fc10544d
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d387229964f95ac5ab5bac0b890c28ce6a6db845
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996671"
---
# <a name="using-the-mqsagent-com-configuration-wizard"></a>使用 MQSAgent COM + 組態精靈
[MQSAgent COM+ 組態精靈] 可以設定 MQSAgent、配接器的 COM+ 應用程式 (MQSeries 元件) 部分。 精靈會設定元件的應用程式識別，以及角色中包含的角色名稱和使用者。 使用 MQSAgent COM + 組態精靈所建立的 MQSAgent COM + 元件的名稱是**MQSAgent2**。  

> [!NOTE]
>  64 位元 Windows server 支援 MQSAgent COM + 應用程式。 它會以 32 位元處理序在 WOW64 下執行。 在 64 位元版本的 Windows Server 上執行的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦可以和已安裝 MQSAgent 的遠端 32 位元電腦通訊。  
> 
> [!NOTE]
>  MQSeries 代理程式與 MQSAgent COM + 組態精靈執行檔**MQSConfigWiz.exe**只有當您從 BizTalk Server 2009 升級到 BizTalk Server，不會安裝。 之後從重新執行的 BizTalk Server 2009 安裝升級到 BizTalk Server，選取**修改**選項，然後選取 其他軟體來安裝這些元件的 MQSeries 代理程式。  

## <a name="to-set-the-application-identity"></a>設定應用程式識別  

-   使用**應用程式識別**MQSAgent COM + 組態精靈，如下所示設定 mqsagent 的應用程式身分識別的頁面：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**互動式的使用者**|選取此選項以使用應用程式識別目前的登入帳戶。|  
    |**本機服務**|將應用程式識別設定為內建服務帳戶。|  
    |**網路服務**|將應用程式識別設定為具有網路存取的內建帳戶。|  
    |**這位使用者**|將應用程式識別設定為指示的使用者名稱。|  

> [!NOTE]
>  不建議您在應用程式識別使用具有系統管理權限的帳戶。 此帳戶必須具備基本的必要權限：MQSeries 佇列的讀取和寫入權限。  

## <a name="to-name-the-role-and-add-users-to-it"></a>命名角色並將使用者加入角色中  

- 使用**角色名稱**MQSAgent COM + 組態精靈 將指派的名稱和使用者角色，如下所示的頁面：  


  |     使用     |                                                                         以進行此動作                                                                          |
  |------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | **角色名稱** |                                                                 鍵入角色的名稱。                                                                  |
  |    **使用者**     |                                                         顯示屬於角色的使用者。                                                          |
  |     **[加入]**      | 新增使用者到角色中。 這些是使用配接器的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服務帳戶。 |

> [!NOTE]
>  僅將要求存取配接器的帳戶新增至角色中。  

## <a name="to-set-the-msdtc-security-configuration-on-the-windows-server-2008-computer-to-no-authentication-required"></a>在 Windows Server 2008 電腦上將「MSDTC 安全性」組態設定為不需要驗證  
 如果 MQSAgent COM + 應用程式安裝在[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]電腦與 MQSeries 配接器 （這與 BizTalk Server 一起安裝） 安裝上[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或是[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]電腦、 上的 MSDTC 安全性組態[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]的電腦必須設為**不需要驗證**。 請依照以下步驟執行，將 MSDTC 安全性組態設定為 [不需要驗證]：  

1.  按一下 **開始**，然後按一下**控制台**。  

2.  按兩下**系統管理工具**。  

3.  按兩下**Microsoft.biztalk.deployment.deployercomponent**來啟動**元件服務**管理介面。  

4.  依序展開**元件服務**，展開**電腦**，然後展開**我的電腦**。  

5.  以滑鼠右鍵按一下**我的電腦**然後按一下**屬性**功能表項目。  

6.  在 [**我的電腦**] 對話方塊中，按一下**MSDTC**索引標籤，然後按一下**的安全性組態**。  

7.  在 **安全性設定**對話方塊中，於**交易管理員通訊**區段中，選取**不需要驗證**。 如果系統提示您使用對話方塊中，按一下**是**重新啟動 MS DTC 服務。  

8.  重新啟動 MS DTC 服務之後，請按一下**確定**然後按一下**確定**以關閉**我的電腦** 對話方塊。  

9. 關閉**元件服務**管理介面。  

## <a name="to-configure-the-mqsagent-runtime-components-to-run-under-an-alternative-set-of-credentials"></a>設定 MQSAgent 執行階段元件在另一組認證上執行  
 MQSAgent COM+ 應用程式包含管理與執行階段的元件。 如果您因為安全性考量，想要將此功能區分為不同的 COM+ 應用程式，請在安裝 MQSAgent COM+ 應用程式的電腦上依照下列步驟執行：  

1.  啟用 MQSAgent COM+ 元件變更。  

    -   按一下 **開始**，然後按一下**控制台**。  

    -   按兩下**系統管理工具**。  

    -   按兩下**Microsoft.biztalk.deployment.deployercomponent**來啟動**元件服務**管理介面。  

    -   依序展開**Microsoft.biztalk.deployment.deployercomponent**，展開**我的電腦**，展開**COM + 應用程式**，以滑鼠右鍵按一下**MQSAgent2** COM + 應用程式然後按一下**屬性**。  

    -   按一下 **進階**索引標籤，然後取消核取**停用變更**。  

    -   按一下 [確定] 。  

2.  為 MQSAgent 執行階段元件建立新的 COM+ 應用程式。  

    -   以滑鼠右鍵按一下**COM + 應用程式**，按一下**新增**，**應用程式**以顯示**COM + 應用程式安裝精靈**按一下**下一步**。  

    -   按一下 **建立空白的應用程式**。  

    -   輸入名稱**MQSAgent2RunTime**，保留預設選項，如**伺服器應用程式**啟用，然後按一下**下一步**。  

    -   選取的選項**此使用者**，輸入適當的帳戶資訊，然後按一下**下一步**。  

        > [!NOTE]
        >  此帳戶應該具備**連接**並**放**和/或**取得**適當的 IBM WebSphere MQ for Windows 佇列上的權限。 您可以設定此帳戶的適當權限**setmqaut**適用於 IBM WebSphere MQ 的命令。 如需詳細資訊**setmqaut**命令，請參閱 IBM WebSphere MQ 文件。  

    -   按一下 [**下一步**上**新增應用程式角色**] 對話方塊。  

    -   按一下 [**下一步**上**將使用者新增至角色**] 對話方塊。  

    -   按一下 **[完成]**。  

3.  將執行階段元件移至新的 COM+ 應用程式  

    -   依序展開**MQSAgent2** COM + 應用程式。  

    -   依序展開**元件**。  

    -   以滑鼠右鍵按一下**mqsagent2.mqsagent.1**元件，再按一下**移動**以顯示**移動元件 (s)**  對話方塊。  

    -   選取**MQSAgent2RunTime**下方**請選取 目的地**，按一下 **確定**。  

    -   重複這些步驟 **[mqsagent2.mqsbroker.1]** 並 **[mqsagent2.mqsproxy.1]** 元件。  

## <a name="see-also"></a>另請參閱  
 [如何設定 MQSeries 配接器傳送和接收處理常式](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md)   
 [設定 MQSeries 配接器](../core/configuring-the-mqseries-adapter.md)