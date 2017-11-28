---
title: "步驟 1-新增應用程式專案和更新的 json |Microsoft 文件"
description: "在 Visual Studio 中，將 BizTalk Server 應用程式專案，並更新 BizTalkServerInventory.json 檔使用的 Dll、 繫結檔案和應用程式-Visual Studio Team Services 的部署序列"
ms.custom: 
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8d4b9773c9c7b23715b5ddae29c3c97f381da5e
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="step-1-add-the-biztalk-server-application-project-in-visual-studio"></a>步驟 1: Visual Studio 中加入 BizTalk Server 應用程式專案

當您建置應用程式使用 Visual Studio Team Services 時，新的 BizTalk 專案檔會建立 –.btaproj。 這個新專案會保存所有的 BizTalk 應用程式您建置和部署使用 VSTS 建置和發行功能。 

BizTalk 應用程式專案包含`BizTalkServerInventory.json`檔案。 在此檔案中，新增 BizTalk 組件，加入 BizTalk 應用程式的繫結檔案，然後設定的部署順序。 

## <a name="before-you-begin"></a>開始之前

* 這些步驟假設您有現有的 BizTalk 專案。 如果沒有，您可以使用 HelloWorld sdk > 範例 (\Program Files (x86) \Microsoft BizTalk Server *yourVersion*\SDK\Samples\Orchestrations\HelloWorld)。 
* 需要您準備好的 BizTalk 專案的 XML 繫結檔案路徑。 
* 知道 VSTS 帳戶、 您的集合和 team 專案的詳細資料。
* 要熟悉 git 概念，包括複製，以及使用儲存機制。 
* 請務必[Feature Pack 2](https://aka.ms/bts2016fp2)安裝。

## <a name="add-the-application-project"></a>新增應用程式專案

1. 在 BizTalk 伺服器上，請在 Visual Studio 中開啟方案 (ProjectName.sln)。 請勿選取 Visual Studio 的 Blend。

2. 在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取**建置**。 請確定您的組建成功。 以滑鼠右鍵按一下您的專案，然後選取**部署**。 請確定您的部署成功。

3. 以滑鼠右鍵按一下您的方案中，選取**新增**，然後選取**加入新的專案**。

4. 選取**BizTalk 專案**索引標籤上，選取**.NET Framework 4.6.1**從下拉式清單中，然後選取**BizTalk Server 應用程式專案**。 輸入名稱 (例如 appProjectHelloWorld)，並選取**確定**:  

    ![新增應用程式專案](../core/media/add-application-project.png)

5. 在 [方案總管] 中，以滑鼠右鍵按一下新加入的應用程式專案 (.btaproj) 中，選取**新增**，選取**參考**。 展開**專案**索引標籤，並檢查您的 BizTalk 專案 （您要部署使用 VSTS 專案）。 選取 [確定]。  
    一旦加入，依序展開**參考**應用程式專案 (例如 appProjectHelloWorld)，以查看 BizTalk 專案在您剛才加入。 

6. 在 [方案總管] 中，以滑鼠右鍵按一下您的應用程式專案 (.btaproj) 中，選取**新增**，選取**現有項目**，和**新增**您繫結的 XML 檔案。

7. 開啟 binding.xml，內容和設定**複製到輸出目錄**至**永遠複製**。 **儲存**您的變更：  

    ![繫結檔案屬性](../core/media/xml-binding-file-properties.png)

8. 選擇性。 以滑鼠右鍵按一下您剛新增的應用程式的專案，然後選取**屬性**。 自訂**應用程式名稱**您想要顯示在 BizTalk 管理中：  

    ![應用程式名稱](../core/media/application-project-name.png)

## <a name="configure-the-json-template"></a>設定的 JSON 範本

1. 在 Visual Studio 中，在應用程式專案 (.btaproj)，開啟`BizTalkServerInventory.json`檔案。 

2. 範本包含下列各節： 

    | | |
    |---|---|
    |BizTalkAssemblies | 在應用程式中使用的組件 |
    |BindingFiles | 您所參考的繫結檔案|
    |DeploymentSequence | 若要安裝元素的順序|
    
    範例範本： 
    
    ![FP1 Json 範本映像 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > 根據您的方案的複雜度，您要在組建中的元素必須參考此 JSON 範本檔案中。

3. 在`BizTalkAssemblies`，將 BizTalk 專案所使用的組件： 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. 在`BindingsFiles`，新增您的 BizTalk 專案的繫結檔案： 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. 在`DeploymentSequence`，這些部署，以及安裝在您想要的順序新增應用程式名稱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]: 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```


6. **儲存**您的變更。 完成時，您的.json 檔案看起來如下： 

    ```
    {
      "$schema": "C:\\Program Files (x86)\\Microsoft BizTalk Server 2016\\Developer Tools\\BizTalkServerAppplicationSchema.json",
      "BizTalkAssemblies": [
        {
          "Name": "HelloWorld",
          "Path": "HelloWorld\\bin\\Release\\HelloWorld.dll"
        }
      ],
      "BindingsFiles": [
        {
          "Name": "HelloWorldBinding",
          "Path": "HelloWorld\\HelloWorldBinding.xml"
        }
      ],
      "DeploymentSequence": [
        "HelloWorld", "HelloWorldBinding"
      ]
    }
    ```

7. **選擇性**。 以滑鼠右鍵按一下您的應用程式專案 (例如 appProjectHelloWorld)，然後選取**屬性**。 您可以設定偵錯或發行版本，為新值。 我們不在這些步驟中，但請留意執行這項操作。  

    ![設定偵錯或發行版本](../core/media/application-project-version.png)

8. 以滑鼠右鍵按一下您的應用程式專案 (例如 appProjectHelloWorld)，然後選取**建置**。 如果成功，zip 檔案中建立 ***yourApplicationProject*\bin\debug**資料夾：  

    ![建立 zip 檔案](../core/media/application-project-zip-file.png)

9. 選取您的方案，然後選取**Team Explorer**  索引標籤。在 VSTS 中，選取**連接**。  

    ![連接到 Team Services](../core/media/connect-team-services.png)

10. 選取 VSTS 帳戶、 您的集合和 team 專案。 選取 [確定]。 如果您尚未建立 VSTS 帳戶，然後建立一個 ([步驟 2： 建立 VSTS 權杖](feature-pack-create-vsts-token.md)提供一些指引)。 一旦建立之後，請返回此步驟中，並連接。  

    ![選取您的集合和專案](../core/media/team-collections-projects.png)

11. 當您連線時，可能會收到提示，要複製這個儲存機制。 選取**複製這個儲存機制**連結。  

    ![複製儲存機制](../core/media/vsts-clone-repository.png)

12. 請注意 URL 和路徑，然後選取**複製**:  

    ![儲存機制路徑](../core/media/clone-repo-paths.png)

完成後，Visual Studio Team 服務部署工作會接受所需的檔案和安裝順序。 

> [!TIP]
> 如果您的專案後再製 git 中進行變更，您可以**階段**您的變更，然後**推送**，全部都在 Visual Studio 內。 

## <a name="what-you-did"></a>您的作法

在 BizTalk 專案中，您可以加入的 BizTalk 應用程式專案 (.btaproj)。 這個專案用來自動化使用 VSTS BizTalk Server 專案的部署。 建立應用程式專案之後，您會加入您的 BizTalk 專案的參考。 然後，您可以更新通知自動化的部署，哪些 Dll 部署，若要使用，哪一個繫結檔案，才能部署應用程式的 JSON 檔案。 

## <a name="next-steps"></a>後續的步驟
[步驟 2： 建立 VSTS 語彙基元](feature-pack-create-vsts-token.md)  
[步驟 3： 建立組建和發行定義](feature-pack-add-build-release-definitions.md)  
[設定環境的語彙基元和變數](configure-environmental-tokens-and-variables-for-automatic-deployment.md)