---
title: 字串運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d73be02-9c93-481f-81e4-39b60bcfa2df
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72e2651c38d3cc69e5c6d7c7d80c6e0d29136033
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966599"
---
# <a name="string-functoids"></a>字串運算質

## <a name="overview"></a>概觀
**字串**運算質可用於管理字串，標準的方式，例如轉換成全部大寫或全部小寫，字串串連，判斷字串長度、 空白字元修剪等等。  

 運算質**大寫**，**小寫**，**大小**，**字串右空白位置修剪**，以及**字串左空白位置修剪**只接受一個輸入的參數。 運算質**字串尋找**，**字串左**，並**字串右**接受兩個輸入參數。 **字串擷取**運算質接受三個輸入，而**字串串連**運算質接受 1 到 100 之間的輸入的參數。  

 兩個**字串**運算質是指在字串中字元的數字位置：**字串擷取**並**字串尋找**。 這些運算質從字元位置 1 開始計數，而不是從 0 開始。  

 這兩個字串修剪運算質**字串左空白位置修剪**並**字串右空白位置修剪**，移除所有泛空白字元 （空格、 定位點，等等） 的左邊或右邊 （因為可能的情況下） 指定的字串。  

## <a name="available-functoids"></a>可用的運算質 
 **字串**運算質為： 

* 小寫
* 大小
* 字串串連
* 字串擷取
* 字串尋找
* 字串左字元回傳
* 字串左空白位置修剪
* 字串右字元回傳
* 字串右空白位置修剪
* 大寫

更多有關這些運算質[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="see-also"></a>另請參閱  
- [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
- **字串運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
