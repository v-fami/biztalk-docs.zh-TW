---
title: 如何安裝 Web 安裝套件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, deploying
- Web services, installing
ms.assetid: c6b38a2f-ad07-4ccd-b267-9e3510df88c3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21fbacd76598a3a86cfa70b4761bc74420afe561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254126"
---
# <a name="how-to-install-the-web-setup-package"></a>如何安裝 Web 安裝套件
使用發佈資料夾的內容，將 Web 服務安裝在目的地電腦上。  
  
### <a name="to-install-the-web-setup-package"></a>若要安裝 Web 安裝套件  
  
1.  將發佈資料夾複製到目的地電腦。  
  
    > [!IMPORTANT]
    >  目的地電腦必須已安裝 BizTalk Server 執行階段，而且必要的 BizTalk 組件必須部署並安裝於全域組件快取中。  
  
2.  執行 .MSI 檔案安裝 Web 服務，並遵循安裝精靈的提示。  
  
    > [!IMPORTANT]
    >  當精靈提示您輸入虛擬目錄時，移除 "_Setup" 尾碼。移除尾碼可確保接收位置的位址符合 Web 服務 .asmx 檔案。  
  
3.  確認虛擬目錄的安全性設定正確，可供授權。  
  
## <a name="see-also"></a>另請參閱  
 [部署在非 Visual Studio 電腦上的已發佈的 Web 服務](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)