---
title: 如何顯示所有管理組件規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7fdec550-6713-4f5f-8c04-d9218bf2df3c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08ec94eb3adb87bf6feaff032e00a61bc9b0fead
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298214"
---
# <a name="how-to-display-all-management-pack-rules"></a>如何顯示所有管理組件規則
您可以使用下列程序來顯示您匯入的管理組件的規則清單。 在 Office Excel 中，您可以檢視的規則清單。  
  
### <a name="to-display-management-pack-rules"></a>若要顯示管理組件規則  
  
1.  在 管理伺服器中，按一下 **程式**，然後按一下  **System Center**。  
  
2.  按一下**命令殼層**。  
  
3.  在命令殼層中，輸入下列命令：   
    `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-SCOMRule | export-csv "c:\rules.csv"`  
  
4.  建立.csv 檔案。 您可以在 Office Excel 中開啟.csv 檔案。  
  
    > [!NOTE]  
    >  在 Office Excel 時，您可能需要指定此.csv 檔案為文字檔。