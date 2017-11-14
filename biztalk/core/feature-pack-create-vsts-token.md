---
title: "步驟 2-建立 VSTS 權杖並安裝代理程式 |Microsoft 文件"
description: "Visual studio，建立 VSTS 安全性存取語彙基元，複製 VSTS 專案，並安裝來自動化部署的 BizTalk Server 專案的組建代理程式"
ms.custom: 
ms.date: 11/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46047f0bb6a536642d503d68bb4f9161ecdf7fc5
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="step-2-create-the-token--install-the-agent"></a>步驟 2： 建立權杖，並安裝代理程式

Visual Studio Team Services 中建立個人存取權杖 (PAT)。 這個語彙基元是您的密碼，並可由 VSTS 組建代理程式來進行驗證。 當您建立它時，才會顯示語彙基元。 在這之後，它不會顯示不再。 因此一旦您建立它，將它儲存到另一個檔案中可記住的位置。 

在 PAT 上的進一歩[驗證個人存取權杖以存取 VSTS 和 TFS](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate)。 

建立權杖之後，您會安裝組建代理程式，並將它設定為使用此權杖。 

## <a name="sign-into-vsts-and-create-the-token"></a>登入 VSTS，並建立語彙基元
1. 移至[https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile)，並使用您的工作或學校帳戶登入。 在您登入後，會列出 VSTS 帳戶。 在下列範例中，此帳戶是**mandiaprojects.visualstudio.com**。  

    ![VSTS 帳戶](../core/media/team-services-accounts.png)

    如果您沒有帳戶，請選取**建立新帳戶**，然後輸入的名稱。 若要管理您的程式碼中，選擇您個人的喜好設定之間**Git 或 Team Foundation 版本控制**。 完成時，會建立新的帳戶，而且類似於站台*https://YourAccountName.visualstudio.com/MyFirstProject*開啟：  

    ![Git 或 TFS](../core/media/git-or-team-foundation.png)

2. 開啟 VSTS 帳戶 (https://*YourAccountName*。 visualstudio.com)。 在右邊的角，選取您的圖示，然後選取**安全性**: 

    ![開啟您的帳戶安全性](../core/media/vsts-account-security.png)

3. **個人存取權杖**會自動開啟。 如果您有現有的代理程式時，加以選取，並確認**代理程式集區 （讀取、 管理）**選取：

    ![代理程式集區的讀取及管理](../core/media/agent-pools-read-manage.png)

    > [!IMPORTANT]
    > 您必須知道存取權杖。 如果您不這麼做，而且沒有任何位置注意它，便無法加以擷取。 在此情況下，建立新的代理程式。 

    如果您沒有現有的代理程式，選取**新增**、 輸入描述、 設定到期日，然後選取您的帳戶。 在**選取範圍**，選取**代理程式集區 （讀取、 管理）**: 

    ![建立新的代理程式-讀取及管理](../core/media/vsts-new-build-agent.png)

    選取**建立語彙基元**。 **請注意語彙基元的值;您需要在未來步驟。**

4. 選取**程式碼**，然後選取**Visual Studio 中的複製**:  

    ![在專案中，選取 程式碼](../core/media/vsts-project-code.png)  

    ![在 Visual Studio 中複製](../core/media/vsts-clone-in-visual-studio.png)

5. Visual Studio 隨即開啟。 在 Visual Studio 中，開啟您的 BizTalk 方案。 

## <a name="install-the-build-agent"></a>安裝組建代理程式

BizTalk 開發電腦上安裝的組建代理程式。 

1. 開啟您的 VSTS 帳戶和專案中，這不是像*https://YourAccountName.visualstudio.com/MyFirstProject*。 選取 [設定] 圖示，然後選取**代理程式佇列**:  

    ![設定 > 代理程式佇列](../core/media/vsts-settings-agent-queues.png)

2. 選取**預設**代理程式，然後選取**下載代理程式**。 選取**下載**按鈕，然後檔案儲存到您**下載**資料夾。

3. 安裝步驟，自動開啟。 請遵循這些步驟最新詳細資料。 以下是一些指導方針： 

    1. 以系統管理員身分開啟 Windows PowerShell。

    2. 若要建立代理程式，請輸入： 

        ```powershell
        PS C:\> mkdir agent ; cd agent  

        PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win7-x64-2.124.0.zip", "$PWD")
        ```
    
        Vsts 代理程式的檔案版本變更。 因此請依照 VSTS 安裝的特定詳細資料。 您到達後輸入，可能需要幾分鐘的提示，以傳回。 

    3. 若要設定代理程式，請輸入： 

        ```powershell
        PS C:\agent> .\config.cmd
        ```

    4. 輸入下列詳細資料：  
        
        | 屬性 | 值 |
        | --- | --- |
        | 伺服器 URL| https://{your-account}.visualstudio.com |
        | 驗證類型 | PAT |
        | 個人存取權杖 | 貼上您 VSTS 語彙基元 |
        | 代理程式集區 | 輸入預設值 |
        | 代理程式名稱 | 輸入預設值 |
        | 取代 | *如果您有現有的代理程式只會顯示* |
        | 工作資料夾 | 輸入預設值 |
        | 以服務方式執行代理程式 | Y |
        | 使用者帳戶 | 這是可以自行決定，但您可能會遇到權限問題。 <br/><br/>請考慮輸入您目前登入的帳戶，也就是本機系統管理員。 |

    5. 完成時，您的 PowerShell 視窗看起來如下：  
    
        ![代理程式安裝](../core/media/vsts-agent-powershell-install.png)

4. 若要查看新的服務開啟 services.msc。 它應執行：  

    ![服務正在執行](../core/media/vsts-service.png)

    如果服務無法啟動，[移除並重新設定代理程式](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows)使用具有更多的權限的帳戶。


## <a name="what-you-did"></a>您的作法

您登入您的 VSTS 帳戶，並建立安全性權杖。 這個安全性權杖就像密碼，並可讓您存取 VSTS 專案。 它只會顯示一次，因此會確定您儲存它。 您也可以複製 VSTS 專案到 Visual Studio 中，然後建立 BizTalk 開發電腦以服務方式執行的代理程式。 此代理程式會使用安全性權杖。 

## <a name="next-steps"></a>後續的步驟
[步驟 3： 建立組建和發行定義](feature-pack-add-build-release-definitions.md)  
[設定環境的語彙基元和變數](configure-environmental-tokens-and-variables-for-automatic-deployment.md)