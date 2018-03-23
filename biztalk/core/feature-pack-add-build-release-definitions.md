---
title: 步驟 3-建立組建和發行定義 |Microsoft 文件
description: 在 VSTS 中，會建立組建定義，以便建置您的 git 或 TFS 儲存機制中的專案，然後建立要部署 BizTalk Server 應用程式的發行定義
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
ms.openlocfilehash: 5ce84071fbc105fd9faddd794792273aae2e76b9
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="step-3-create-the-build-and-release-definition"></a>步驟 3： 建立組建和發行定義

組建和發行定義是 Visual Studio Team Services 的工作，並可能由 VSTS 系統管理員。組建定義建置您的專案，在您的 git 儲存機制和發行定義將其部署到 BizTalk Server 環境。 

## <a name="before-you-begin"></a>開始之前
完成[步驟 2-建立 VSTS 語彙基元，並安裝代理程式](feature-pack-create-vsts-token.md)。

## <a name="add-the-build-tasks"></a>加入建置工作
1. 在專案中，選取**組建與版本**。 [組建] 索引標籤隨即開啟。 建立**新增**定義：

    ![新的組建定義](../core/media/vsts-new-definition.png)

2. 選取**空**範本，然後選取**套用**:  

    ![選取空白的範本](../core/media/vsts-emtpy-template.png)
 
3. 設定**代理程式佇列**為預設值： 

    ![選擇預設佇列](../core/media/vsts-select-agent-queue.png)

4. 在**階段 1**、 加入工作中，選取**Visual Studio 建置**，然後選取**新增**:

    ![加入 VS 建置工作](../core/media/vsts-add-visual-studio-task.png)

5. 按一下 Visual Studio 建置的工作只需要加入，並設定下列屬性：  

    | 屬性 | 設定為 |
    | --- | --- | 
    | 顯示名稱 | *YourProjectName*建置方案 * *\*.sln | 
    | Visual Studio 版本 | Visual Studio 2015 | 
    | MSBuild 架構 | MSBuild x86 | 

6. 在**階段 1**、 加入工作中，選取**發行組建成品**，然後選取**新增**: 

    ![加入 VS 建置工作](../core/media/vsts-add-publish-build-task.png)

7. 選取**發行成品**工作，並輸入慣用**顯示名稱**。 如**發行路徑**，選取**...**按鈕，然後選擇應用程式專案的資料夾 (例如 appProjectHelloWorld)。 選取 [確定]。

8. **成品名稱**可以是您想要的任何項目。 選取**儲存**。 

9. 移至**觸發程序**，並設定**觸發狀態**至**啟用**:  

    ![加入 VS 建置工作](../core/media/vsts-continuous-integration.png)

10. **儲存並佇列**來測試您的組建定義。 當您排入佇列時，系統會提示您為代理程式佇列和您的分支。 選取**預設**代理程式佇列，然後選擇您的分支。 選取**佇列**。  

11. 新組建會啟動，且您可以選取它，以便檢查成功或失敗。 

## <a name="add-the-release-tasks"></a>將發行工作

建置成功時，發行定義部署到 BizTalk Server 應用程式。 

1. 選取**版本**索引標籤上，選取**新定義**。 

2. 選取**空**範本，然後選取**套用**:

    ![加入空白的範本](../core/media/vsts-empty-release-template.png)

3. 變更**環境名稱**至**Dev**，或任何您要呼叫它。 

4. 選取**新增成品**，選取您的專案，您的組建定義，然後選取**新增**: 

5. 移至**工作**索引標籤上，將新工作： 

    ![將發行工作](../core/media/vsts-new-release-tasks.png)

6. 從清單中，篩選的結果，請選取**BizTalk Server 應用程式部署**工作，並選取**新增**:  

    ![新增 BizTalk 部署工作](../core/media/vsts-biztalk-application-deployment-task.png)

    如果**BizTalk Server 應用程式部署**ins't 列出，然後將它安裝在[部署 BizTalk 應用程式](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application)。

7. 選取**部署**工作，並輸入值： 

    **作業名稱**： 您的選項: ***建立新的 BizTalk 應用程式**： 將新的應用程式部署。 如果應用程式已經存在，它會解除安裝目前的應用程式 （完全停止），並會安裝新的應用程式。 如果已啟用持續整合，它會自動重新部署應用程式更新儲存機制中時。 
        * **更新現有的 BizTalk 應用程式**： 將變更，例如結構描述、 附加至正在執行的應用程式。 它不需要完整的重新部署應用程式。
        * **安裝 BizTalk Server 應用程式**:[安裝的應用程式](../core/how-to-install-a-biztalk-application.md)，輸入 BizTalk 管理的電腦名稱和部署封裝路徑。

        ![Deploy operations](../core/media/vsts-deploy-operations.png)

    **應用程式名稱**： 您輸入的文字將會在 BizTalk 管理中的應用程式名稱。 請勿**不**輸入 BizTalk Application 1。

    **部署套件**： 選取您的應用程式專案，zip 檔案，然後選取**確定**。 

8. 選取**代理程式階段**工作。 選取**預設**代理程式佇列。 **儲存** 您的變更。

9. 選取**釋放** > **建立發行**:  

    ![版本中，建立發行](../core/media/vsts-create-release.png)

10. 選取**佇列**。 檢查狀態，依序按一下 [版本] 連結。 如果失敗，錯誤訊息中顯示。 如果成功，應用程式會加入至 BizTalk 管理主控台。 

## <a name="what-you-did"></a>您的作法

在 VSTS 中，您可以建立組建 Git 或 Team Foundation 版本控制 （無論您選擇） 內的應用程式的組建定義。 原始檔控制中變更時，所做的變更會自動偵測，您可以將其推送。 在建置完成之後，您會建立應用程式部署至 BizTalk Server 中，您可以在 BizTalk Server 管理 中看到的發行定義。 

## <a name="next-step"></a>下一步
在此步驟中，您已完成。 如果您想要的話，您可以在 BizTalk XML 繫結檔案中，建立環境的語彙基元，並建立符合環境的語彙基元的 VSTS 中的變數。 請參閱[設定環境的語彙基元和變數](configure-environmental-tokens-and-variables-for-automatic-deployment.md)詳細資料。 