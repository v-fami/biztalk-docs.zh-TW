---
title: 步驟 2-建立 VSTS 權杖及安裝代理程式 |Microsoft Docs
description: Visual studio，建立 VSTS 安全性存取權杖，複製您的 VSTS 專案，並安裝組建代理程式自動部署您的 BizTalk Server 專案
ms.custom: ''
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d26a218b6de83b1ab2e5a2dd46be215dcbb0f49
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979343"
---
# <a name="step-2-create-the-token--install-the-agent"></a>步驟 2： 建立權杖，並安裝代理程式

Visual Studio Team Services 中建立個人存取權杖 (PAT)。 此權杖是您的密碼，並由 VSTS 組建代理程式用來驗證。 當您在建立時，才會顯示此語彙基元。 在那之後，它不會顯示不再。 因此一旦您建立它，將它儲存到另一個可記住的位置中的檔案。 

深入了解在 PAT[驗證適用於 VSTS 和 TFS 的個人存取權杖以存取](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate)。 

建立權杖之後，您會安裝組建代理程式，並將它設定為使用此權杖。 

## <a name="before-you-begin"></a>開始之前
完整[步驟 1-新增應用程式專案，並更新 json](feature-pack-add-application-project.md)。

## <a name="sign-into-vsts-and-create-the-token"></a>登入 VSTS，並建立權杖
1. 移至[ https://app.vsaex.visualstudio.com/go/profile ](https://app.vsaex.visualstudio.com/go/profile)，並使用您的公司或學校帳戶登入。 登入之後，會列出您的 VSTS 帳戶。 在下列範例中，帳戶是**mandiaprojects.visualstudio.com**。  

    ![VSTS 帳戶](../core/media/team-services-accounts.png)

    如果您還沒有帳戶，請選取**建立新帳戶**，然後輸入名稱。 若要管理您的程式碼，請選擇您個人的喜好設定之間**Git 或 Team Foundation 版本控制**。 完成時，會建立新的帳戶，和類似的站台*https://YourAccountName.visualstudio.com/MyFirstProject*開啟：  

    ![Git 或 TFS](../core/media/git-or-team-foundation.png)

2. 開啟您的 VSTS 帳戶 (https://<em>YourAccountName</em>。 visualstudio.com)。 在右側角，選取您的圖示，然後選取**安全性**: 

    ![開啟您的帳戶安全性](../core/media/vsts-account-security.png)

3. **個人存取權杖**會自動開啟。 如果您有現有的代理程式時，加以選取，並確認**代理程式集區 （讀取、 管理）** 選取：

    ![代理程式集區-讀取與管理](../core/media/agent-pools-read-manage.png)

    > [!IMPORTANT]
    > 您必須知道的存取權杖。 如果您不這麼做，並沒有記下任何位置，便無法加以擷取。 在此情況下，建立新的代理程式。 

    如果您沒有現有的代理程式，請選取**新增**、 輸入描述，設定到期日，然後選取您的帳戶。 在 **選取範圍**，選取**代理程式集區 （讀取、 管理）**: 

    ![建立新的代理程式-讀取與管理](../core/media/vsts-new-build-agent.png)

    選取 **建立權杖**。 **請注意語彙基元的值;您必須在未來的步驟。**

4. 選取 **程式碼**，然後選取**在 Visual Studio 中的複製**:  

    ![在專案中，選取 程式碼](../core/media/vsts-project-code.png)  

    ![在 Visual Studio 中複製](../core/media/vsts-clone-in-visual-studio.png)

5. Visual Studio 隨即開啟。 在 Visual Studio 中，開啟您的 BizTalk 方案。 

## <a name="install-the-build-agent"></a>安裝組建代理程式

BizTalk 開發電腦上安裝組建代理程式。 使用部署群組，如果您想要部署到的所有 BizTalk 伺服器上安裝組建代理程式。 下列步驟會示範如何在單一電腦上安裝組建代理程式。 如需有關使用部署群組的詳細資訊，請參閱 <<c0> [ 部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)。

1. 開啟您的 VSTS 帳戶和專案中，這不是想*https://YourAccountName.visualstudio.com/MyFirstProject*。 選取 [設定] 圖示，然後選取**代理程式佇列**:  

    ![設定 > 代理程式佇列](../core/media/vsts-settings-agent-queues.png)

2. 選取 **預設**代理程式，然後選取**下載代理程式**。 選取 **下載**按鈕，然後將檔案儲存到您**下載**資料夾。

3. 安裝步驟自動開啟。 請遵循這些步驟的最新詳細資料。 以下是一些指引： 

   1. 系統管理員身分開啟 Windows PowerShell。

   2. 若要建立代理程式，請輸入： 

       ```powershell
       PS C:\> mkdir agent ; cd agent  

       PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win7-x64-2.124.0.zip", "$PWD")
       ```

       Vsts 代理程式的檔案版本變更。 因此請遵循 VSTS 安裝步驟的特定詳細資料。 您按下之後輸入，可能需要數分鐘，返回提示字元。 

   3. 若要設定代理程式，請輸入： 

       ```powershell
       PS C:\agent> .\config.cmd
       ```

   4. 輸入下列詳細資料：  


      |        屬性        |                                                                      ReplTest1                                                                       |
      |------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
      |       伺服器 URL       |                                                     https://{your-account}.visualstudio.com                                                      |
      |  驗證類型   |                                                                       PAT                                                                        |
      | 個人存取權杖  |                                                              貼上您的 VSTS 權杖                                                               |
      |       代理程式集區       |                                                              輸入預設值                                                               |
      |       代理程式名稱       |                                                              輸入預設值                                                               |
      |        取代         |                                                  *只會顯示如果您有現有的代理程式*                                                   |
      |      工作資料夾       |                                                              輸入預設值                                                               |
      | 以服務方式執行代理程式 |                                                                        Y                                                                         |
      |      使用者帳戶      | 這是由您決定，但您可能會遇到權限問題。 <br/><br/>請考慮輸入您目前已登入的帳戶，也就是本機系統管理員。 |


   5. 完成時，您的 PowerShell 視窗看起來如下所示：  

       ![代理程式安裝](../core/media/vsts-agent-powershell-install.png)

4. 若要查看新的服務開啟 services.msc。 它應該執行：  

    ![服務正在執行](../core/media/vsts-service.png)

    如果服務無法啟動，請[移除並重新設定代理程式](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows)使用具有更多的權限的帳戶。


## <a name="what-you-did"></a>您的作法

您登入您的 VSTS 帳戶，並建立安全性權杖。 這個安全性權杖就像是使用密碼，並可讓您存取您的 VSTS 專案。 它只會顯示一次，因此要確定您儲存它。 您也可以複製您的 VSTS 專案至 Visual Studio，然後建立 BizTalk 開發電腦以服務形式執行的代理程式。 此代理程式會使用安全性權杖。 

## <a name="next-steps"></a>後續的步驟
[步驟 3： 建立組建和發行定義](feature-pack-add-build-release-definitions.md)  
[設定環境權杖和變數](configure-environmental-tokens-and-variables-for-automatic-deployment.md)