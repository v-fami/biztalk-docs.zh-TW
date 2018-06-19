---
redirect_url: /biztalk/core/feature-pack-add-application-project/
redirect_document_id: true
ROBOTS: NOINDEX
title: 設定自動部署的 JSON 範本 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 0b7755a6-5a5a-4a6b-8f99-ac12a5fbf3d4
caps.latest.revision: 4
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 10d85b625d759af675ecc1a38d540da8a304ba43
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
ms.locfileid: "24054518"
---
# <a name="configure-the-json-template-for-automatic-deployment"></a>設定自動部署的 JSON 範本


當您建置應用程式使用 Visual Studio Team Services 時，新的 BizTalk 專案檔會建立 – (.btaproj)。 這個新的專案會保存所有的 BizTalk 應用程式使用 VSTS 所建立。 

您的專案包含`BizTalkServerInventory.json`檔案。 在此檔案中，加入您的 BizTalk 組件、 將 BizTalk 應用程式的繫結檔案新增及設定的部署順序。 

本主題說明如何更新 json 檔案。 

## <a name="add-assemblies-binding-files-and-deployment-sequence"></a>加入組件、 繫結檔案和部署順序

1. 開啟`BizTalkServerInventory.json`檔案中您**BizTalk Server 應用程式**專案 (.btaproj)。

2. 範本包含下列各節： 

    | | |
    |---|---|
    |BizTalkAssemblies | 在應用程式中使用的組件 |
    |BindingFiles | 您所參考的繫結檔案|
    | DeploymentSequence | 若要安裝元素的順序|
    
    範例範本： 
    
    ![FP1 Json 範本映像 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > 根據您的方案的複雜度，您要在組建中的元素必須參考此 JSON 範本檔案中。

3. 在`BizTalkAssemblies`，將您的 BizTalk 應用程式所使用的組件： 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. 在`BindingsFiles`，新增您的 BizTalk 應用程式的繫結檔案： 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. 在`DeploymentSequence`，部署並安裝在您想要的順序新增應用程式名稱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]: 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```
    
6. **儲存**您的變更。 

完成後，Visual Studio Team 服務部署工作會接受所需的檔案和安裝順序。 

## <a name="next-step"></a>下一步
[設定語彙基元和變數](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md)繫結檔案部署至多個相同的 BizTalk 應用程式中[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]s。

 