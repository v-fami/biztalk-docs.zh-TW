---
title: "建立環境的語彙基元 & 變數 |Microsoft 文件 」"
description: "繫結檔案更新為使用環境語彙基元，並在 VSTS 來自動化部署的 BizTalk Server 應用程式中建立變數"
ms.custom: 
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d84fa393410e3084c87e762140530a45b0b78b5
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a>設定環境的語彙基元和自動部署的變數
使用 Visual Studio Team Services (VSTS) 變數，在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]繫結檔案。

## <a name="overview"></a>概觀
在 VSTS 環境中，您可以加入變數，並設為值。 例如，您可以建立*sendPortPath*變數，並將其值設定在實體資料夾您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

內[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]應用程式繫結檔案，可設定的變數可以是任何項目內的 XML 標記，例如接收位置名稱、 主機、 傳送埠的 URI，等等。 

這些變數專屬於您 VSTS 的環境，而且可用來部署至多個相同的應用程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。 

我們會示範如何加入 VSTS 變數在繫結檔案中，以及如何建立在 VSTS 中的變數。 

## <a name="add-variables-to-the-binding-file"></a>將變數加入至繫結檔案

1. 開啟應用程式繫結檔案：

    ![開啟 繫結檔案](../core/media/biztalk-feature-pack-1-binding-1.png)

2. 尋找您想要變更的項目：

    ![選取的項目](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. 移除填入的值，以取代您變數： `$(YourValue)`。 例如，輸入`$(SendPort1)`: 

    ![繫結檔案](../core/media/biztalk-feature-pack-1-binding-3.png)

4. 完成時，儲存繫結檔案，並將它加入至您的 JSON 建置範本 (步驟[步驟 1： 新增應用程式專案 （& s） 更新.json 範本](feature-pack-add-application-project.md))。

## <a name="create-the-variables-in-vsts"></a>建立於 VSTS 中的變數

1. VSTS 帳戶中，選取**組建與版本**，然後選取**版本**。

2. 選取您**發行定義**，然後選取**變數**:  

    ![繫結檔案](../core/media/vsts-release-variables.png)

3. 選取**新增**，並建立的變數名稱和值：   

    ![設定變數](../core/media/environment-specific-variables.png)

4. **儲存**您的變更。 起始部署時，這些值會加入從繫結檔案。

## <a name="see-also"></a>另請參閱
[使用 Visual Studio Team Services 中設定自動部署](configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  
[設定 Feature Pack](configure-the-feature-pack.md)