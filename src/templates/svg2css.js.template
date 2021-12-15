"use strict";
exports.__esModule = true;
exports.svgTocss = void 0;
function addfun(str, array) {
    if (str && array) {
        for (var i in array) {
            str += " " + i + "='" + array[i] + "'";
        }
        return str;
    }
}
function getReg(str, reg) {
    var match = str.match(reg);
    if (match && match[1]) {
        return match[1];
    }
    else {
        return '';
    }
}
//列表压缩
function cutlist(d) {
    if (d) {
        var newstr = void 0;
        var arr = str2arr(d, ' ');
        var newarr = new Array();
        for (var i in arr) {
            var nstr = doCutdown(arr[i]);
            newarr.push(nstr);
        }
        newstr = newarr.join(' ');
        return newstr;
    }
}
//单个字符处理
function round_single(str) {
    var arr = str2arr(str, '.');
    var newarr = new Array();
    arr.forEach(function (_item, i) {
        if (i == 0) {
            newarr.push(arr[i]);
        }
        else {
            var letter = arr[i].match(/[^0-9][A-z]*/g);
            if (letter != null && letter.length > 1) {
                newarr.push(arr[i]);
            }
            else {
                var num1 = void 0;
                var match = arr[i].match(/([0-9]*)([A-z]*)([0-9]*)/);
                if (match && match[1].length >= 3) {
                    var match_1 = '1.' + match[1];
                    match_1 = parseFloat(match_1).toFixed(2); //保留2位小数
                    num1 = match_1.split('.')[1];
                }
                else {
                    num1 = (match && match[1]) || "";
                }
                newarr.push(num1 + (match && match[2]) + (match && match[3]));
            }
        }
    });
    return newarr.join('.');
}
//列表字符处理
function round_link(str) {
    var arr = str2arr(str, '-');
    var newarr = new Array();
    for (var i in arr) {
        newarr.push(round_single(arr[i]));
    }
    return newarr.join('-');
}
//单个压缩
function doCutdown(str) {
    var arr = str2arr(str, '-');
    //-号连接符类型  211.06521c-39.036245-39.722612-85.269714-71.26541-137.216891
    if (arr.length > 1) {
        str = round_link(str);
    }
    //单字符类型  455.241026[z]
    else {
        str = round_single(str);
    }
    return str;
}
// 字符串转数组
function str2arr(str, mark) {
    var arr = [];
    if (!str.includes(mark)) {
        arr.push(str);
    }
    else {
        arr = str.split(mark);
    }
    return arr;
}
// svg转css（多色）
function svgTocss(code, color) {
    //去除无用信息 p-id
    code = code.replace(/p\-id\=\"[0-9]*\"/g, '');
    //清除格式
    code = code.replace(/\'/g, '"');
    code = code.replace(/\n/g, '');
    code = code.replace(/\r/g, '');
    code = code.replace(/\s/g, ' ');
    code = code.replace(/\s+/g, ' ');
    //path
    var reg = /path(\s{0,}fill\=\"(\#{0,1}[A-z0-9]*)?\")?\s{1,}d\=\"[A-z0-9\s\.\-\,]*\"(\s{0,}fill\=\"(\#{0,1}[A-z0-9]*)?\")?/g;
    var regd = /d\=\"([A-z0-9\s\.\-\,]*)\"/;
    var coded = 'd';
    var path = code.match(reg);
    var pathname = 'path';
    if (!path) {
        //polygon  尝试读取形状
        reg = /polygon(\s{0,}fill\=\"(\#{0,1}[A-z0-9]*)?\")?\s{1,}points\=\"[A-z0-9\s\.\-\,]*\"(\s{0,}fill\=\"(\#{0,1}[A-z0-9]*)?\")?/g;
        regd = /points\=\"([A-z0-9\s\.\-\,]*)\"/;
        coded = 'points';
        path = code.match(reg);
        pathname = 'polygon';
        if (!path) {
            return false;
        }
    }
    var path_str = '';
    for (var i in path) {
        //d代码
        path_str += '%3E%3C' + pathname;
        var d = void 0;
        d = getReg(path[i], regd);
        d = d.replace(/\,/g, ' ');
        d = d.replace(/(^\s*)|(\s*$)/g, '');
        //压缩
        path_str += " " + coded + "='" + cutlist(d) + "'";
        //填色
        var cpre = '%23';
        var fill = void 0;
        if (color && color[i]) {
            fill = color;
            fill = fill.replace('#', '%23');
        }
        else {
            reg = /fill\=\"(\#{0,1})([A-z0-9]*)?\"/;
            var fill_arr = path[i].match(reg);
            if (fill_arr && fill_arr[2]) {
                fill = cpre + fill_arr[2].toLowerCase();
            }
            else {
                fill = '';
            }
        }
        path_str += " fill='" + fill + "'";
        path_str += '/';
    }
    var add = new Array();
    //width
    reg = /width\=\"([0-9\.]*)(px)?\"/;
    add['width'] = getReg(code, reg);
    //height
    reg = /height\=\"([0-9\.]*)(px)?\"/;
    add['height'] = getReg(code, reg);
    var css = 'data:image/svg+xml,%3Csvg';
    //viewBox
    reg = /viewBox\=\"([0-9\s]*)\"/;
    add['viewBox'] = getReg(code, reg);
    //xmlns
    add['xmlns'] = 'http://www.w3.org/2000/svg';
    css = addfun(css, add);
    css += path_str;
    css += '%3E%3C/svg%3E';
    return css;
}
exports.svgTocss = svgTocss;
